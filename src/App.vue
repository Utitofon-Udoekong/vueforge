<script setup lang="ts">
import { Drawer, DrawerContent } from "@progress/kendo-vue-layout";
import { DropDownButton, Button as kbutton } from "@progress/kendo-vue-buttons";
import { useRouter } from "vue-router";
import { ref } from "vue";
const router = useRouter();
const expanded = ref(true);
const selectedId = ref(0);
const position = "start";
const mode = "push";

const items = [
  {
    text: "Boards",
    icon: "k-i-inbox",
    selected: true,
    data: {
      path: "/",
    },
  },
  {
    text: "Templates",
    icon: "k-i-border-left",
    data: {
      path: "/templates",
    },
  },
  {
    text: "Settings",
    icon: "k-i-gear",
    data: {
      path: "/settings",
    },
  },
  {
    text: "Collapse",
    icon: "k-i-arrow-chevron-right",
  },
];
const teams = [
  {
    text: "Team 1",
  },
  {
    text: "Team 2",
  },
];
const onSelect = (e: any) => {
  console.log(e);
  selectedId.value = e.itemIndex;
  router.push(items[e.itemIndex].data?.path);
};
const handleClick = () => {
  expanded.value = !expanded.value;
};
</script>

<template>
  <div>
    <div class="custom-toolbar flex justify-between px-4 py-4 border-b border-gray-200">
      <div class="logo">
        <p>Logo</p>
      </div>
      <div>
        <DropDownButton
          :items="teams"
          text="My Team"
          fillMode="flat"
          icon="ungroup"
          class="text-red-500"
        />
        <kbutton class="" themeColor="dark">Logout</kbutton>
      </div>
    </div>
    <Drawer
      :expanded="expanded"
      :position="position"
      :mode="mode"
      :items="
        items.map((item, index) => ({
          ...item,
          selected: index === selectedId,
        }))
      "
      @select="onSelect"
    >
      <DrawerContent>
        <router-view />
      </DrawerContent>
    </Drawer>
  </div>
</template>
