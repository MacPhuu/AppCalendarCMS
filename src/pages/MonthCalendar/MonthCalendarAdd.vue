<template>
  <q-header elevated class="bg-white flex items-center" style="height: 64px">
    <q-toolbar class="flex row reverse">
      <q-icon class="text-black" name="account_circle" size="30px" />
      <span class="text-black q-mx-md">Admin</span>
    </q-toolbar>
  </q-header>
  <div class="q-ma-xl">
    <div class="breadscrum">
      <q-breadcrumbs>
        <q-breadcrumbs-el label="Thông tin sự kiện" />
        <q-breadcrumbs-el label="Âm lịch" />
      </q-breadcrumbs>
    </div>
    <div class="Save-btn">
      <q-btn
        label="Lưu"
        no-caps
        size="17px"
        color="negative"
        @click="Save"
      ></q-btn>
    </div>
    <div class="separator"></div>
  </div>
  <div class="PageBody">
    <div class="row q-my-md">
      <div class="col-6 q-pr-md">
        <div class="text-h6">Ngày diễn ra</div>
        <q-input outlined="" v-model="date" class="text-h6">
          <template v-slot:prepend>
            <q-icon name="event" class="cursor-pointer">
              <q-popup-proxy
                cover
                transition-show="scale"
                transition-hide="scale"
              >
                <q-date v-model="date" mask="YYYY-MM-DD">
                  <div class="row items-center justify-end">
                    <q-btn v-close-popup label="Close" color="primary" flat />
                  </div>
                </q-date>
              </q-popup-proxy>
            </q-icon>
          </template>
        </q-input>
      </div>
      <div class="col-6 q-pl-md">
        <div class="text-h6">Thứ</div>
        <q-select
          behavior="menu"
          outlined
          class="text-h6"
          v-model="day_in_week"
          :options="day_options"
          popup-content-class="text-h6"
        />
      </div>
    </div>
    <div class="row q-my-md">
      <div class="col-6 q-pr-md">
        <div class="text-h6">Tên sự kiện</div>
        <q-input
          outlined
          class="text-h6"
          v-model="name"
          placeholder="Nhập tiêu đề..."
        />
      </div>
      <div class="col-6 q-pl-md"></div>
    </div>
    <div>
      <div class="text-h6">Nội dung</div>
      <q-editor
        v-model="qeditor"
        height="429px"
        :dense="$q.screen.lt.md"
        :toolbar="[
          [
            {
              label: $q.lang.editor.align,
              icon: $q.iconSet.editor.align,
              fixedLabel: true,
              list: 'only-icons',
              options: ['left', 'center', 'right', 'justify'],
            },
          ],
          ['bold', 'italic', 'strike', 'underline', 'subscript', 'superscript'],
          ['token', 'hr', 'link', 'custom_btn'],
          ['print', 'fullscreen'],
          [
            {
              label: $q.lang.editor.formatting,
              icon: $q.iconSet.editor.formatting,
              list: 'no-icons',
              options: ['p', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'code'],
            },
            {
              label: $q.lang.editor.fontSize,
              icon: $q.iconSet.editor.fontSize,
              fixedLabel: true,
              fixedIcon: true,
              list: 'no-icons',
              options: [
                'size-1',
                'size-2',
                'size-3',
                'size-4',
                'size-5',
                'size-6',
                'size-7',
              ],
            },
            {
              label: $q.lang.editor.defaultFont,
              icon: $q.iconSet.editor.font,
              fixedIcon: true,
              list: 'no-icons',
              options: [
                'default_font',
                'arial',
                'arial_black',
                'comic_sans',
                'courier_new',
                'impact',
                'lucida_grande',
                'times_new_roman',
                'verdana',
              ],
            },
            'removeFormat',
          ],
          ['quote', 'unordered', 'ordered', 'outdent', 'indent'],

          ['undo', 'redo'],
          ['viewsource'],
        ]"
        :fonts="{
          arial: 'Arial',
          arial_black: 'Arial Black',
          comic_sans: 'Comic Sans MS',
          courier_new: 'Courier New',
          impact: 'Impact',
          lucida_grande: 'Lucida Grande',
          times_new_roman: 'Times New Roman',
          verdana: 'Verdana',
        }"
      />
    </div>
  </div>
</template>
<script>
import { defineComponent, ref } from "vue";
const day_options = [
  "Thứ hai",
  "Thứ ba",
  "Thứ tư",
  "Thứ năm",
  "Thứ sáu",
  "Thứ bảy",
  "Chủ nhật",
];

export default defineComponent({
  name: "MonthCalendar",
  setup() {
    return {
      date: ref(""),
      name: ref(""),
      day_in_week: ref(""),
      day_options,
      qeditor: ref(""),
    };
  },
  methods: {
    Save() {},
  },
});
</script>
<style scoped>
.breadscrum {
  position: absolute;
  font-size: 17px;
  top: 100px;
  left: 268px;
  background-color: white;
  padding: 0 30px 0 30px;
}
.separator {
  border-bottom: 3px solid #e9eaec;
}
.Save-btn {
  position: absolute;
  top: 92px;
  right: 30px;
  background-color: white;
  padding: 0 30px 0 30px;
}
.PageBody {
  margin: 57px;
}
</style>
