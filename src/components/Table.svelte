<script>
	import { todos } from "../store";
	import { scale } from "svelte/transition";

	const complete = (title) => {
		//filtro para deletar o item do array
		const filtro = $todos.filter((e) => e.title !== title);

		//gravando o novo array na loja todos
		$todos = filtro;
	};
</script>

{#if $todos.length > 0}
	<table class="table mt-4">
		<thead>
			<tr>
				<th scope="col">#</th>
				<th scope="col">Título</th>
				<th scope="col">Descrição</th>
				<th scope="col" class="d-flex justify-content-end">Ações</th>
			</tr>
		</thead>
		<tbody>
			{#each $todos as todo, i}
				<tr
					in:scale={{ duration: 500, opacity: 0, start: 1.5 }}
					out:scale={{ duration: 500, opacity: 0, start: 1 }}
				>
					<th scope="row">{i + 1}</th>
					<td>{todo.title}</td>
					<td>{todo.description}</td>
					<td class="d-flex justify-content-end">
						<button
							on:click={(e) => complete(todo.title)}
							class="btn btn-danger">Completo</button
						>
					</td>
				</tr>
			{/each}
		</tbody>
	</table>
{:else}
	<div class="mt-4">
		<h6>Você não tem tarefas...</h6>
	</div>
{/if}
