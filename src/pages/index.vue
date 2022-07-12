<script setup lang="ts">
import {
  Card,
  CardHeader,
  CardBody,
  CardTitle,
  CardSubtitle,
  CardImage,
  CardActions,
  Avatar,
} from "@progress/kendo-vue-layout";
import { Button as kbutton } from "@progress/kendo-vue-buttons";

const cards = [
  {
    thumbnailSrc:
      "https://www.telerik.com/kendo-vue-ui/components/layout/assets/card/bg_flag.jpg",

    headerTitle: "bg_traditions",

    headerSubtitle: "Bulgaria, Europe",

    commentsExpanded: false,

    postLiked: false,

    comments: [
      {
        text: "uygwyhhwuike",
        likes: 57,
      },
      {
        text: "ccoieodrjis",
        likes: 84,
      },
      {
        text: "iou0jmk ",
        likes: 19,
      },
    ],

    newCommentTextValue: "",

    postLikes: 174,

    scrollViewItems: {
      url: "https://www.telerik.com/kendo-vue-ui/components/layout/assets/card/rose_festival.jpg",
    },
  },

  {
    thumbnailSrc:
      "https://www.telerik.com/kendo-vue-ui/components/layout/assets/card/rila_lakes.jpg",
    headerTitle: "bg_mountains",
    headerSubtitle: "Bulgaria, Europe",
    commentsExpanded: false,
    postLiked: false,
    comments: [
      {
        text: "oujroiejior",
        likes: 5,
      },
      {
        text: "wregvtrf",
        likes: 53,
      },
      {
        text: "badoo",
        likes: 15,
      },
    ],
    newCommentTextValue: "",
    postLikes: 962,
    scrollViewItems: {
      url: "https://www.telerik.com/kendo-vue-ui/components/layout/assets/card/rila.jpg",
    },
  },
];
</script>

<template>
  <div class="p-5">
    <p class="title font-semibold text-3xl capitalize">Boards</p>
    <div class="flex justify-between flex-wrap">
      <div v-for="(card, index) in cards" :key="index">
        <Card class="w-[260px] mt-[15px] shadow-md">
          <CardHeader class="k-hbox bg-transparent">
            <avatar type="image" size="medium" shape="circle">
              <img class="w-[45px] h-[45px]" :src="card.thumbnailSrc" />
            </avatar>

            <div>
              <CardTitle class="mb-2">
                {{ card.headerTitle }}
              </CardTitle>

              <CardSubtitle>
                <p>{{ card.headerSubtitle }}</p>
              </CardSubtitle>
            </div>
          </CardHeader>

          <CardImage
            :src="card.scrollViewItems.url"
            class="h-[185px] max-w-full"
          />

          <CardActions class="flex justify-between">
            <div>
              <kbutton
                :fill-mode="'flat'"
                :icon="card.postLiked ? 'heart' : 'heart-outline'"
              >
              </kbutton>

              <kbutton :fill-mode="'flat'" :icon="'comment'"> </kbutton>

              <kbutton :fill-mode="'flat'" :icon="'share'"> </kbutton>
            </div>

            <span class="text-[13px] self-center text-[#656565]">
              {{ card.postLikes }} likes
            </span>
          </CardActions>

          <CardBody v-if="card.commentsExpanded">
            <div>
              <div style="margin-bottom: 8px; padding: 0 16px">
                <div v-for="(comment, index) in card.comments" :key="index">
                  <div style="display: flex; justify-content: space-between">
                    <div
                      style="padding: 4px 0; align-items: center; display: flex"
                    >
                      <Avatar
                        :type="'text'"
                        :rounded="'full'"
                        style="color: white"
                        :size="'small'"
                      >
                        <span>SS</span>
                      </Avatar>

                      <div style="display: flex; flex-direction: column">
                        <span
                          style="
                            font-size: 13px;
                            font-weight: bold;
                            max-width: 100px;
                            word-break: break-all;
                          "
                        >
                          {{ comment.text }}
                        </span>

                        <span class="time">
                          1s ago

                          <span style="margin-left: 8px">
                            {{ comment.likes }} like
                          </span>
                        </span>
                      </div>
                    </div>

                    <kbutton :fill-mode="'flat'">
                      <span
                        :class="
                          comment && comment.likes > 0
                            ? 'k-icon k-i-heart'
                            : 'k-icon k-i-heart-outline'
                        "
                      />
                    </kbutton>
                  </div>
                </div>
              </div>
            </div>

            <div class="k-hbox" style="padding: 16px 16px 0">
              <textarea
                class="k-textarea"
                placeholder="Comment..."
                style="
                  resize: none;
                  border-radius: 10px;
                  padding: 5px;
                  font-size: 10px;
                "
              />

              <kbutton
                :fill-mode="'flat'"
                :theme-color="'primary'"
                style="margin-left: 10px; border-radius: 10px"
              >
                Post
              </kbutton>
            </div>
          </CardBody>
        </Card>
      </div>
    </div>
  </div>
</template>
