<template>
    <div>
    Текущая дата: {{ currentDate }}
    </div>
</template>

<script>
export default {
  data(){
        return{
            currentDate: new Date().toLocaleDateString('ru-RU')
        }
        }
}
</script>