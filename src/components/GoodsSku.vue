<script setup lang="ts">
import { reactive } from 'vue';

/** 分隔符 */
const SPLITER = '-';

interface Spec {
  id: string;
  name: string;
  values: SpecValue[];
}

interface SpecValue {
  name: string;
  desc: string;
  picture: string | null;
  selected?: boolean;
  disabled?: boolean;
}

interface Sku {
  id: string;
  price: string | number;
  oldPrice: string | number;
  inventory: number;
  specs: SkuSpec[];
  [key: string]: any;
}

interface SkuSpec {
  name: string;
  valueName: string;
}

interface Goods {
  specs: Spec[];
  skus: Sku[];
  [key: string]: any;
}

const props = withDefaults(
  defineProps<{
    goods: Goods;
  }>(),
  {
    goods: () => ({ specs: [], skus: [] }) as Goods,
  }
);
const localSpecs = reactive([...props.goods.specs]);

/**
 * 切换选中状态
 * @param spec 所有规格项
 * @param value 当前规格项
 */
const handleSpecSelect = (spec: Spec, value: SpecValue) => {
  if (value.disabled) return;

  if (value.selected) {
    value.selected = false;
  } else {
    spec.values.forEach(v => (v.selected = false));
    value.selected = true;
  }

  updateDisabledStatus();
  checkCompleteSelection();
};

/**
 * 计算幂集
 * @param arr 原始集合
 */
const getPowerSet = <T,>(arr: T[]) => {
  return Array.from({ length: 2 ** arr.length }, (_, i) => arr.filter((_, j) => i & (1 << j)));
};

/** 生成有效路径字典对象 */
const getPathMap = (goods: Goods) => {
  const pathMap: Record<string, string[]> = {};
  const effectiveSkus = goods.skus.filter(sku => sku.inventory > 0);
  effectiveSkus.forEach(sku => {
    const selectedValArr = sku.specs.map(spec => spec.valueName);
    const valueArrPowerSet = getPowerSet(selectedValArr);
    valueArrPowerSet.forEach(arr => {
      const key = arr.join(SPLITER);
      if (pathMap[key]) {
        pathMap[key].push(sku.id);
      } else {
        pathMap[key] = [sku.id];
      }
    });
  });
  return pathMap;
};
const pathMap = getPathMap(props.goods);

// 初始化禁用状态
const initDisabledStatus = () => {
  localSpecs.forEach(spec => {
    spec.values.forEach(value => (value.disabled = !pathMap[value.name]));
  });
};
initDisabledStatus();

/** 获取当前选中的规格集合 */
const getSelectedValues = (specs: Spec[]) => {
  return specs.map(spec => {
    const selectedValue = spec.values.find(value => value.selected);
    return selectedValue?.name;
  });
};

/** 切换时更新禁用状态 */
const updateDisabledStatus = () => {
  localSpecs.forEach((spec, index) => {
    const selectedValues = getSelectedValues(localSpecs);
    spec.values.forEach(val => {
      selectedValues[index] = val.name;
      const key = selectedValues.filter(value => value).join(SPLITER);
      if (pathMap[key]) {
        val.disabled = false;
      } else {
        val.disabled = true;
      }
    });
  });
};

const emit = defineEmits<{
  (
    e: 'change',
    sku: {
      skuId: string;
      price: string | number;
      oldPrice: string | number;
      inventory: number;
      specsText: string;
    }
  ): void;
}>();

/** 检查是否完成规格选择 */
const checkCompleteSelection = () => {
  const selectedValues = getSelectedValues(localSpecs).filter(value => value);
  if (selectedValues.length === localSpecs.length) {
    const key = selectedValues.join(SPLITER);
    const skuId = pathMap[key][0];
    const sku = props.goods.skus.find(item => item.id === skuId);
    if (!sku) return;
    emit('change', {
      skuId: sku.id,
      price: sku.price,
      oldPrice: sku.oldPrice,
      inventory: sku.inventory,
      specsText: sku.specs.map(spec => `${spec.name}：${spec.valueName}`).join(' '),
    });
  }
};
</script>

<template>
  <div class="goods-sku">
    <dl v-for="spec in localSpecs" :key="spec.id">
      <dt>{{ spec.name }}</dt>
      <dd>
        <template v-for="value in spec.values" :key="value.name">
          <!-- 图片类型规格 -->
          <img
            v-if="value.picture"
            :class="{ selected: value.selected, disabled: value.disabled }"
            :src="value.picture"
            :title="value.name"
            @click="handleSpecSelect(spec, value)"
          />
          <!-- 文字类型规格 -->
          <span
            v-else
            :class="{ selected: value.selected, disabled: value.disabled }"
            @click="handleSpecSelect(spec, value)"
          >
            {{ value.name }}
          </span>
        </template>
      </dd>
    </dl>
  </div>
</template>

<style scoped lang="scss">
@mixin sku-state-mixin {
  border: 1px solid #ddd;
  margin-right: 10px;
  cursor: pointer;
  &:hover {
    border-color: #27ba9b;
  }
  &.selected {
    border-color: #27ba9b;
  }
  &.disabled {
    opacity: 0.6;
    border-style: dashed;
    cursor: not-allowed;
  }
}

.goods-sku {
  padding: 20px;
  dl {
    display: flex;
    padding-bottom: 10px;
    align-items: center;
    dt {
      width: 40px;
      color: #999;
    }
    dd {
      flex: 1;
      color: #666;
      > img {
        width: 50px;
        @include sku-state-mixin;
      }
      > span {
        display: inline-block;
        height: 30px;
        line-height: 30px;
        padding: 0 20px;
        @include sku-state-mixin;
      }
    }
  }
}
</style>
