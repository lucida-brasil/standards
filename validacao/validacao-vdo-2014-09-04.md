---
data: 04-09-2014
ambiente: homologação
objetivo: implementação da camada de dados
---

#Validação VDO - Equipamentos portáteis


#Definição do objeto global

Especificado no item dois da documentação.

- Em escopo global (`window`)
- Antes da chamada do GTM, de preferencia no `<head>`

## Implementação atual

### Declaração

O objeto está declarado dentro de uma função anônima no callback do evento `$(document).ready` depois do core do GTM:

```html
<script type="text/javascript">
	$(document).ready(function() {
		var customData = {
			'site': { 
				'name': 'Venda Online - Seguro Equipamentos Portáteis - Home', 
				'type': 'VDO', 
				'campaign': 'VDO', 
				'product': 'seguroep', 
				'version': 'v1' 
			}
		};
	});
</script>
``` 

Essa declaração não permite que a camada de dados seja lida por outros scripts, como o GTM, a implementação correta é:

### Especificação do template

Em nenhumas das páginas testadas em homologação possui o atributo `customData.page.template`, essa informação é de extrema importancia para identicicarmos com segunrança, sem dependencia da URL, em qual etapa do funil o usuário se encontra.

## Exemplo de implementação

Esse scrpipt deve ser incluído antes do GTM, de preferência entre as tags `<head>` e `</head>`:

```html
<script type="text/javascript">
	var customData = {
			'site' : {
				'name': 'Venda Online - Seguro Equipamentos Portáteis - Preço', //alterar de acordo com a página
				'type': 'VDO', 
				'campaign': 'VDO', 
				'product': 'seguroep', 
				'version': 'v1'
			},
			'page' : {
				'template' : 'orcamento' //alterar de acordo com a página
			}
		};
</script>
```
download do documento: [VDO - Especificação camada de dados.pdf](VDO-Especificacao_camada_de_dados.pdf?raw=true)