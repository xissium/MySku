<script setup lang="ts">
import GoodsSku from '@/components/GoodsSku.vue';
import { reactive, ref } from 'vue';

const goods = reactive({
  specs: [
    {
      name: '颜色',
      id: '1369139574067957762',
      values: [
        {
          name: '黑色',
          picture:
            'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
          desc: '',
        },
        {
          name: '蓝色',
          picture:
            'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
          desc: '',
        },
      ],
    },
    {
      name: '尺寸',
      id: '1369141324204216321',
      values: [
        {
          name: '30cm',
          picture: null,
          desc: '',
        },
        {
          name: '20cm',
          picture: null,
          desc: '',
        },
        {
          name: '10cm',
          picture: null,
          desc: '',
        },
      ],
    },
    {
      name: '产地',
      id: '1369141916305723393',
      values: [
        {
          name: '日本',
          picture: null,
          desc: '',
        },
        {
          name: '中国',
          picture: null,
          desc: '',
        },
      ],
    },
  ],
  skus: [
    {
      id: '1369155862131642369',
      skuCode: 'goods-sku-001',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 0,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
      specs: [
        {
          name: '颜色',
          valueName: '蓝色',
        },
        {
          name: '尺寸',
          valueName: '20cm',
        },
        {
          name: '产地',
          valueName: '中国',
        },
      ],
    },
    {
      id: '1369155863389933570',
      skuCode: 'goods-sku-007',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99654,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
      specs: [
        {
          name: '颜色',
          valueName: '黑色',
        },
        {
          name: '尺寸',
          valueName: '20cm',
        },
        {
          name: '产地',
          valueName: '中国',
        },
      ],
    },
    {
      id: '1369155864430120962',
      skuCode: 'goods-sku-003',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99706,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
      specs: [
        {
          name: '颜色',
          valueName: '蓝色',
        },
        {
          name: '尺寸',
          valueName: '10cm',
        },
        {
          name: '产地',
          valueName: '中国',
        },
      ],
    },
    {
      id: '1369155865461919746',
      skuCode: 'goods-sku-009',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99926,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
      specs: [
        {
          name: '颜色',
          valueName: '黑色',
        },
        {
          name: '尺寸',
          valueName: '10cm',
        },
        {
          name: '产地',
          valueName: '中国',
        },
      ],
    },
    {
      id: '1369155866451775490',
      skuCode: 'goods-sku-005',
      price: '128.00',
      oldPrice: '210.00',
      inventory: 99797,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
      specs: [
        {
          name: '颜色',
          valueName: '蓝色',
        },
        {
          name: '尺寸',
          valueName: '30cm',
        },
        {
          name: '产地',
          valueName: '中国',
        },
      ],
    },
    {
      id: '1369155867420659714',
      skuCode: 'goods-sku-011',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99843,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
      specs: [
        {
          name: '颜色',
          valueName: '黑色',
        },
        {
          name: '尺寸',
          valueName: '30cm',
        },
        {
          name: '产地',
          valueName: '中国',
        },
      ],
    },
    {
      id: '1369155868389543937',
      skuCode: 'goods-sku-002',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99429,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
      specs: [
        {
          name: '颜色',
          valueName: '蓝色',
        },
        {
          name: '尺寸',
          valueName: '20cm',
        },
        {
          name: '产地',
          valueName: '日本',
        },
      ],
    },
    {
      id: '1369155869354233857',
      skuCode: 'goods-sku-008',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 0,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
      specs: [
        {
          name: '颜色',
          valueName: '黑色',
        },
        {
          name: '尺寸',
          valueName: '20cm',
        },
        {
          name: '产地',
          valueName: '日本',
        },
      ],
    },
    {
      id: '1369155870306340866',
      skuCode: 'goods-sku-004',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99936,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
      specs: [
        {
          name: '颜色',
          valueName: '蓝色',
        },
        {
          name: '尺寸',
          valueName: '10cm',
        },
        {
          name: '产地',
          valueName: '日本',
        },
      ],
    },
    {
      id: '1369155871241670658',
      skuCode: 'goods-sku-010',
      price: '128.00',
      oldPrice: '200.00',
      inventory: 99952,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
      specs: [
        {
          name: '颜色',
          valueName: '黑色',
        },
        {
          name: '尺寸',
          valueName: '10cm',
        },
        {
          name: '产地',
          valueName: '日本',
        },
      ],
    },
    {
      id: '1369155872197971970',
      skuCode: 'goods-sku-006',
      price: '148.00',
      oldPrice: '190.00',
      inventory: 99805,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/2d5ba800-1868-48c8-9213-1a5f8965a05b.png',
      specs: [
        {
          name: '颜色',
          valueName: '蓝色',
        },
        {
          name: '尺寸',
          valueName: '30cm',
        },
        {
          name: '产地',
          valueName: '日本',
        },
      ],
    },
    {
      id: '1369155873162661889',
      skuCode: 'goods-sku-012',
      price: '148.00',
      oldPrice: '210.00',
      inventory: 99645,
      picture:
        'http://yjy-xiaotuxian-dev.oss-cn-beijing.aliyuncs.com/picture/2021-04-05/cd6c46b6-b944-4479-b547-cdee294568a1.png',
      specs: [
        {
          name: '颜色',
          valueName: '黑色',
        },
        {
          name: '尺寸',
          valueName: '30cm',
        },
        {
          name: '产地',
          valueName: '日本',
        },
      ],
    },
  ],
});

const specsText = ref('');
const handleChange = (sku: any) => {
  specsText.value = sku.specsText;
};
</script>

<template>
  <div class="wrapper">
    <GoodsSku :goods="goods" @change="handleChange" />
    <div style="height: 30px; color: goldenrod">{{ specsText }}</div>
  </div>
</template>

<style scoped lang="scss">
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  min-height: 90vh;
}
</style>
