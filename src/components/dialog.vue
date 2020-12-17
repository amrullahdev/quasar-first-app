<template>
	<q-page>
		<q-dialog v-model="confirm" persistent>
			<q-card>
				<q-card-section class="row items-center">
					<q-avatar icon="help"  text-color="primary"/>
					<span class="q-ml-sm">Menghapus Data ini ?</span>
				</q-card-section>
				<q-card-actions align="right">
					<q-btn flat label="Batalkan" color="primary" v-close-popup />
					<q-btn flat label="Hapus" color="primary" v-close-popup @click="go" />
				</q-card-actions>
			</q-card>
		</q-dialog>
	</q-page>
</template>
<script>
	import {nv} from '../services/emit.js'
	export default{
		data(){
			return {
				dataHapus:'',
				confirm:false,
			}
		},
		mounted(){
			nv.$on('test',(data)=>{
				this.confirm=true,
				this.dataHapus=data
			})
		},
		methods:{
			go(){
				nv.$emit('go',this.dataHapus)
			}
		}
	}
</script>
