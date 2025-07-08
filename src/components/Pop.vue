<script setup>
import { ref } from 'vue'
import { Icon } from '@iconify/vue'

const showPop = ref(false)
const closePopup = () => {
  showPop.value = false
}
</script>

<template>
  <!-- 右下角的icon -->
  <Icon
    icon="mdi:alert-circle"
    class="icon-wrapper"
    width="48"
    height="48"
    @click="showPop = true"
  />

  <!-- 彈窗 -->
  <div v-if="showPop" class="popWrap" @click.self="closePopup">
    <div class="popWrap-content">
      <button class="close-btn" @click.self="closePopup">✖</button>
      <h2>意見反饋</h2>
      <div class="title">
        <label>
          <div>
            <span class="required">*</span>
            <span>類別</span>
          </div>
          <select required>
            <option selected>請選擇類別</option>
            <option>2</option>
          </select>
        </label>
      </div>
      <div class="title">
        <label>
          <div>
            <span class="required">*</span><span>標題</span><span class="note">（限30字符內）</span>
          </div>
          <input type="text" name="" id="" placeholder="請輸入標題" />
        </label>
      </div>
      <div class="title">
        <div>
          <span class="required">*</span><span>描述</span><span class="note">（限300字符內）</span>
          <input type="text" name="" id="" placeholder="請描述您的意見/問題" />
        </div>
      </div>
      <div class="title">
        <div><span>參考圖片</span><span class="note">（僅支持PNG、JPG格式，每張5MB內）</span></div>
        <div class="upload-box">
          <span class="plus-icon">+</span>
        </div>
      </div>
      <div class="note">可提供意見/問題截圖（上傳數量0/3）</div>

      <button class="submit" @click.self="closePopup">提交</button>
    </div>
  </div>
</template>

<style scoped>
/* icon */
.icon-wrapper {
  position: fixed;
  bottom: 50px;
  right: 60px;
  z-index: 9999;
}
.icon-wrapper:hover {
  cursor: pointer;
}
/* 彈窗 */
.popWrap {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.4);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}
.popWrap-content {
  position: relative;
  background: white;
  padding: 20px;
  border-radius: 8px;
  width: 600px;
  height: 500px;
  max-width: 90%;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}
.close-btn {
  position: absolute;
  top: 12px;
  right: 12px;
  background: transparent;
  border: none;
  font-size: 20px;
  cursor: pointer;
  color: #999;
}
.close-btn:hover {
  color: #333;
}
.required {
  color: red;
  font-weight: bold;
}
.title {
  font-size: 18px;
}
.title label {
  display: block;
}
.note {
  color: #999;
}
select {
  width: 100%;
  appearance: none;
  padding: 10px;
  border: 1px solid #d9dbe0;
  border-radius: 6px;
  background-color: white;
  color: #1f1f1f;
  font-size: 14px;
  outline: none;
  transition: border-color 0.2s;
  background-image: url("data:image/svg+xml,%3Csvg width='10' height='7' viewBox='0 0 10 7' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%23999' stroke-width='1.5' fill='none' fill-rule='evenodd'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 12px center;
  background-size: 12px;
}
option {
  color: #1f1f1f;
}
input {
  width: 100%;
  appearance: none;
  padding: 10px;
  border: 1px solid #d9dbe0;
  border-radius: 6px;
  background-color: white;
  color: #1f1f1f;
  font-size: 14px;
  outline: none;
}
select:invalid {
  color: #aaa;
}
.upload-box {
  width: 120px;
  height: 120px;
  border: 2px dashed #d3d6de;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  background-color: white;
  transition: border-color 0.2s;
}
.plus-icon {
  font-size: 32px;
  color: #a0a4ad;
}
.submit {
  background-color: #d5e5f7;
  width: 100%;
  color: rgb(73, 145, 226);
  border: none;
  font-size: 14px;
  padding: 5px;
  cursor: pointer;
  margin: 5px 0;
}
</style>
