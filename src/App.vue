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
									{{ prefix }}
								</li>
							</ul>
							<br />
							<input class="form-control" type="text" placeholder="Digite o prefixo " />
						</div>
					</div>
				</div>
				<div class="col-md">
					<h5>Sufixos <span class="badge badge-info">{{ sufixes.length }}</span></h5>
					<div class="card">
						<div class="card-body">
							<ul class="list-group">
								<li class="list-group-item" v-for="sufix in sufixes" v-bind:key="sufix">
									{{ sufix }}
								</li>
							</ul>
							<br />
							<input class="form-control" type="text" placeholder="Digite o sufixo " />
						</div>
					</div>
				</div>
			</div>

			<br/>
			<h5>Domínios <span class="badge badge-info">{{ domains.length }}</span></h5>
			<div class="card">
				<div class="card-body">
					<ul class="list-group">
						<li class="list-group-item" v-for="domain in domains" v-bind:key="domain">
							{{ domain.name }}
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
import 'bootstrap/dist/css/bootstrap.css';
import 'font-awesome/css/font-awesome.css';

export default {
	name: 'app',
	data: function() {
		return {
			prefixes: ['Air', 'Jet', 'Flight', 'Emirates', 'Tam'],
			sufixes: ['Hub', 'Station', 'Mart', 'Fly', 'Airlines'],
			domains: [
				{
					name: 'AirHub'
				},
				{
					name: 'AirStation'
				},
				{
					name: 'AirMart'
				},
				{
					name: 'AirFly'
				},
				{
					name: 'AirAirlines'
				},
				{
					name: 'JetHub'
				},
				{
					name: 'JetStation'
				},
				{
					name: 'JetMart'
				},
				{
					name: 'JetFly'
				},
				{
					name: 'JetAirlines'
				},
				{
					name: 'FlightHub'
				},
				{
					name: 'FlightStation'
				},
				{
					name: 'FlightMart'
				},
				{
					name: 'FlightFly'
				},
				{
					name: 'FlightAirlines'
				},
				{
					name: 'EmiratesHub'
				},
				{
					name: 'EmiratesStation'
				},
				{
					name: 'EmiratesMart'
				},
				{
					name: 'EmiratesFly'
				},
				{
					name: 'EmiratesAirlines'
				},
				{
					name: 'TamHub'
				},
				{
					name: 'TamStation'
				},
				{
					name: 'TamMart'
				},
				{
					name: 'TamFly'
				},
				{
					name: 'TamAirlines'
				}
			],
		};
	}
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
