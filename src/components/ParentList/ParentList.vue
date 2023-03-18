<template>
  <div>
    <div class="itemsBlock">
      <div class="selectedList">
        <ul v-if="leftItems.id">
          <li>
            {{ leftItems.name }}
          </li>
        </ul>
        <span v-else>Select item for Show</span>
      </div>
      <div class="selectedList">
        <ul v-if="reightItems.length > 0">
          <li v-for="item in reightItems" :key="item.id">
            {{ item.name }}
          </li>
        </ul>
        <span v-else>Select item for Show</span>
      </div>
    </div>

    <ItemsList @selectedItem="handleItem" />
  </div>
</template>

<script>
import { reactive } from 'vue';
import ItemsList from '../ItemsList/ItemsList.vue';

export default {
  components: { ItemsList },
  setup() {
    const handleItem = (data) => {
      if (data.e.target.closest('.left') !== null) {
        console.log(data.name, data.id);
        leftItems.id = data.id;
        leftItems.name = data.name;
      } else if (data.e.target.closest('.right') !== null) {
        reightItems.push({ name: data.name, id: data.id });
        console.log(reightItems.length);
      }
    };

    const leftItems = reactive([{}]);
    const reightItems = reactive([]);

    return {
      handleItem,
      leftItems,
      reightItems,
    };
  },
};
</script>

<style src="./_parentList.scss" lang="scss" scoped></style>
