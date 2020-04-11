<template>
	<view>
		<calendar @onCancel="onCancel" @onConfirm="onConfirm" :startDate="startDate" :endDate="endDate" :defaultValue="pickerDate">
		    {{pickerDate}}
		</calendar>
	</view>
</template>

<script>
	import calendar from '@/components/calendar/calendar.vue'
	export default {
		data(){
			return {
				pickerDate:new Date()
			}
		},
		components:{
		        calendar
		    }
	}
</script>

<style>
</style>
