<script>
	import shortid from 'shortid';
	import { todos, saveStorage } from '~/store';
	let title = ''

	function createToDo() {
		if (!title || !title.trim()) return;

		$todos.unshift({
			id: shortid.generate(),
			title
		})
		$todos = $todos // 할당연산자를 통한 반응성 유지
		saveStorage() // 스토리지에 todos 저장

		title = ''
		console.log($todos)
	}
</script>

<div class="create-todo">
	<input
			bind:value={title}
			type="text"
			class="form-control"
			on:keyup={(e) => {
					if (e.key === 'Enter') createToDo()
			}}/>
	<button class="btn btn-primary" on:click={createToDo}>Create</button>
</div>

<style lang="scss">
	.create-todo {
		display: flex;
		margin-top: 50px;
		.btn {
			width: 130px;
			height: 50px;
			font-weight: 700;
			margin-left: 10px;
			flex-shrink: 0;
		}
	}
</style>