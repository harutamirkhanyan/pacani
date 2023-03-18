<template>
  <div class="list">
    <ul class="left">
      <li
        v-for="item in listOne"
        :key="item.id"
        @click="sendInfo(item, $event)"
      >
        {{ item.name }}
      </li>
    </ul>
    <ul class="right">
      <li
        v-for="item in listTwo"
        :key="item.id"
        @click="sendInfo(item, $event)"
      >
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  emits: ['selectedItem'],
  setup(_, { emit }) {
    const selectedItem = reactive({
      name: '',
      id: null,
      e: '',
    });

    const sendInfo = (item, e) => {
      selectedItem.name = item.name;
      selectedItem.id=item.id
      selectedItem.e = e;
      emit('selectedItem', selectedItem);
    };

    const listOne = ref([
      {
        'id': 1,
        'name': 'Shoes 1',
      },
      {
        'id': 2,
        'name': 'Shoes 2',
      },
      {
        'id': 3,
        'name': 'Shoes 3',
      },
      {
        'id': 4,
        'name': 'Shoes 4',
      },
      {
        'id': 5,
        'name': 'T-shirt 1',
      },
      {
        'id': 6,
        'name': 'T-shirt 2',
      },
      {
        'id': 7,
        'name': 'T-shirt 3',
      },
      {
        'id': 8,
        'name': 'T-shirt 4',
      },
    ]);

    const listTwo = ref([
      {
        'id': 11,
        'name': 'Jacket 1',
      },
      {
        'id': 12,
        'name': 'Jacket 2',
      },
      {
        'id': 13,
        'name': 'Jacket 3',
      },
      {
        'id': 14,
        'name': 'Jacket 4',
      },
      {
        'id': 15,
        'name': 'Hoodie 1',
      },
      {
        'id': 16,
        'name': 'Hoodie 2',
      },
      {
        'id': 17,
        'name': 'Hoodie 3',
      },
      {
        'id': 18,
        'name': 'Hoodie 4',
      },
    ]);

    return {
      listOne,
      listTwo,
      sendInfo,
      selectedItem,
    };
  },
};
</script>
<style src="./_itemsList.scss" lang="scss"></style>
