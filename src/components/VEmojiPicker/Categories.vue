<template>
  <div id="Categories">
    <div
      :class="[{ 'active': index === active }, 'category']"
      v-for="(categorie, index) in categories"
      :key="index"
      @click="onSelect(index)" >
      <VSvg :name="categorie.icon"/>
    </div>
  </div>
</template>

<script>
import VSvg from './VSvg';

export default {
  name: "Categories",
  components: {
    VSvg
  },
  data: () => ({
    categories: [
      { name: "Frequenty", icon: "frequenty" },
      { name: "Peoples", icon: "peoples" },
      { name: "Nature", icon: "nature" },
      { name: "Foods", icon: "foods" },
      { name: "Activity", icon: "activity" },
      { name: "Objects", icon: "objects" },
      { name: "Places", icon: "places" },
      { name: "Symbols", icon: "symbols" },
      { name: "Flags", icon: "flags" }
    ],
    active: 1
  }),
  methods: {
    onSelect(index) {
      this.active = index;

      const _category = this.categories[index];
      this.$emit("select", _category);
    }
  }
};
</script>

<style lang="scss" scoped>
#Categories {
  display: flex;
  width: 100%;
  flex-direction: row;
  align-items: center;
  border-bottom: 1px solid #e4e4e4;
  background: #F0F0F0;
  color: white;
}

.category {
  flex: 1;
  padding: 5px 0;
  text-align: center;
  cursor: pointer;

  & > img {
    width: 22px;
    height: 22px;
  }

  &:hover {
    filter: saturate(3);
  }
}

.active {
  border-bottom: 3px solid #009688;
  filter: saturate(3);
}
</style>

