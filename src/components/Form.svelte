<script>
	import { todos } from "../store";

	let title, description;

	const saveTodo = (e) => {
		//salvando todos
		$todos = [...$todos, { title, description }];

		//limpo valor das variáveis
		title = "";
		description = "";
	};
</script>

<form on:submit={(e) => saveTodo()} class="row mt-4">
	<!-- title -->
	<div class="col-md-4">
		<input
			type="text"
			class="form-control shadow"
			placeholder="Título"
			bind:value={title}
			required
		/>
	</div>

	<!-- description -->
	<div class="col-md-4">
		<input
			type="text"
			class="form-control shadow"
			placeholder="Descrição"
			bind:value={description}
			required
		/>
	</div>

	<!-- submit -->
	<div class="col-md-4">
		<button class="btn btn-primary w-100 shadow">Adicionar</button>
	</div>
</form>
