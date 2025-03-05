<script>
export default {
    props: {
        contacts: { type: Array, default: [] }, // danh sách liên hệ
        activeIndex: { type: Number, default: -1 }, // chỉ số của liên hệ đang được chọn
    },
    emits: ["update:activeIndex"], // sự kiện được phát ra khi chỉ số liên hệ được chọn thay đổi
    methods: {
        updateActiveIndex(index) {
            this.$emit("update:activeIndex", index);
        }
    }
};
</script>
<template>
    <ul class="list-group">
        <li class="list-group-item" v-for="(contact, index) in contacts" :key="contact._id"
            :class="{ active: index === activeIndex }" @click="updateActiveIndex(index)">
            {{ contact.name }}
        </li>
    </ul>
</template>