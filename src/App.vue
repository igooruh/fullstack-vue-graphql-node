<template>
<!-- Está div deve ter em todo html devido a mesma ser um root. Todo html da page deve ser criado dentro da mesma -->
  <div> 

    <div class="slogan">
      <section class="text-center">
        <h1>NameGator</h1>
        <h6 class="text-secondary">Gerador de nomes utilizando vue.js, GraphQL e Node.js</h6>
      </section>

      <section class="template-view">
        <div class="container">
			<div class="row">
				<div class="col-md">
					<h5>Prefixos <span class="badge badge-info">{{ prefixes.length }}</span></h5>
					<div class="card">
						<div class="card-body">
							<ul class="list-group">
								<li class="list-group-item" v-for="prefix in prefixes" v-bind:key="prefix">
									<div  class="row">
										<div class="col-md">
											{{ prefix }}
										</div>
										<div class="col-md text-right">
											<button title="Excluir prefixo" class="btn btn-info" v-on:click="deletePrefix(prefix)">
												<span class="fa fa-trash"></span>
											</button>
										</div>
									</div>
								</li>
							</ul>
							<br />
							<div class="input-group">
								<input class="form-control" type="text" v-model="prefix" v-on:keyup.enter="addPrefixes(prefix)" placeholder="Digite o prefixo " />
								<div class="input-group-append">
									<button title="Incluir prefixo" class="btn btn-info" v-on:click="addPrefixes(prefix)">
										<span class="fa fa-plus"></span>
									</button>
								</div>
							</div>
						</div>
					</div>
				</div>
				<div class="col-md">
					<h5>Sufixos <span class="badge badge-info">{{ sufixes.length }}</span></h5>
					<div class="card">
						<div class="card-body">
							<ul class="list-group">
								<li class="list-group-item" v-for="sufix in sufixes" v-bind:key="sufix">
									<div class="row">
										<div class="col-md">
											{{ sufix }}
										</div>
										<div class="col-md text-right">
											<button title="Excluir sufixo" class="btn btn-info" v-on:click="deleteSufix(sufix)">
												<span class="fa fa-trash"></span>
											</button>
										</div>
									</div>
								</li>
							</ul>
							<br />
							<div class="input-group">
								<input class="form-control" type="text" v-model="sufix" v-on:keyup.enter="addSufixes(sufix)" placeholder="Digite o sufixo" />
								<div class="input-group-append">
									<button title="Incluir sufixo" class="btn btn-info" v-on:click="addSufixes(sufix)">
										<span class="fa fa-plus"></span>
									</button>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>

			<br/>
			<h5>Domínios <span class="badge badge-info">{{ domains.length }}</span></h5>
			<div class="card">
				<div class="card-body">
					<ul class="list-group">
						<li class="list-group-item" v-for="domain in domains" v-bind:key="domain.name">
							<div class="row">
								<div class="col-md">
									{{ domain.name }}
								</div>
								<div class="col-md text-right">
									<a class="btn btn-info" v-bind:href="domain.checkout" target="_blank">
										<span class="fa fa-shopping-cart"></span>
									</a>
								</div>
							</div>
						</li>
					</ul>
				</div>
			</div>
        </div>
      </section>
    </div>

  </div>
</template>

<script>
'use strict';
import 'bootstrap/dist/css/bootstrap.css';
import 'font-awesome/css/font-awesome.css';

export default {
	name: 'app',
	data: function() {
		return {
			prefix: '',
			sufix: '',
			prefixes: ['Air', 'Jet', 'Emirates', 'Tam'],
			sufixes: ['Hub', 'Station', 'Fly', 'Airlines'],
		};
	},

	methods: {
		addPrefixes(prefix) {
			this.prefixes.push(prefix);
			this.prefix = '';
		},

		deletePrefix(prefix) {
			this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
		},

		addSufixes(sufix) {
			this.sufixes.push(sufix);
			this.sufix = '';
		},

		deleteSufix(sufix) {
			this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
		},
	},

	computed: {
		domains() {
			const domains = [];
			for(const prefix of this.prefixes) {
				for(const sufix of this.sufixes) {
					const name = prefix + sufix;
					const URL = name.toLowerCase();
					const checkout = `https://checkout.hostgator.com.br/?a=add&sld=${URL}&tld=.com`;
					domains.push({
						name,
						checkout
					});
				}
			}
			return domains;
		}
	},

	// Lifecycle component
	// A resolution to list
	/* created() {
		this.domains = this.generate();
	} */
};
</script>

<style>

.slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}

.template-view {
  background-color: #F1F1F1;
  padding-top: 30px;
  padding-bottom: 30px;
}

</style>
