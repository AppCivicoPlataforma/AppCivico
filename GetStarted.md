Primeiros passos
===================

### Introdução
----------

Este tutorial tem como objetivo apresentar exemplos de como recuperar dados abertos disponíveis na Nuvem Cívica. 


### Como fazer uma requisição
As informações da Nuvem Cívica são disponibilizadas por meio de *webservices* utilizando arquitetura [REST] ( Representational State Transfer). 

Todos os *endpoints* da plataforma possuem a mesma **URL Base**, seguida do nome da API específica:

>  - **API Saúde:** http://mobile-aceite.tcu.gov.br/mapa-da-saude/
>  - **API Escolas:** http://mobile-aceite.tcu.gov.br/nossaEscolaRS/

O detalhamento de cada método disponível nas API's pode ser encontrada em [EscolasAPI.md] e [EstabelecimentosAPI.md].

#### Requisição
Como exemplo, vamos testar uma requisição simples na **API de remédios**, que pesquisa dados de medicamentos fabricados no Brasil e registrados pela ANVISA:

 > **GET**  -  `http://mobile-aceite.tcu.gov.br/mapa-da-saude/rest/remedios?parametro=valor`
 > [(Ver documentação)](https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EstabelecimentosAPI.md#rem%C3%A9dios-1)

De acordo com a documentação, um dos parâmetros aceitoss por esta requisição é o `produto`, indicando o nome comercial do remédio. Assim, para efetuar uma busca pelo remédio "Paracetamol", a seguinte requisição deve ser feita:

> **GET** - http://mobile-aceite.tcu.gov.br/mapa-da-saude/rest/remedios?produto=paracetamol

Obs: Você pode clicar no *link* acima e verificar o retorno das informações!
#### Retorno
Como observado, a requisição acima retorna uma lista de resultados em formato **JSON** com todos os produtos encontrados dado o parâmetro informado. Um exemplo de um trecho do retorno de produto:

```json
{
  "codBarraEan": "7896181921547",
  "principioAtivo": "CLORIDRATO DE TRAMADOL",
  "cnpj": "53.162.095\/0001-06",
  "laboratorio": "BIOSINT\u00c9TICA FARMAC\u00caUTICA LTDA",
  "codGgrem": "521113010057106",
  "registro": "1121304480023",
  "produto": "CLORIDRATO DE TRAMADOL + PARACETAMOL",
  "apresentacao": "37,5 MG + 325 MG COM REV CT BL AL PLAS TRANS X 10",
  "classeTerapeutica": "N02A0 - ANALG\u00c9SICOS NARC\u00d3TICOS",
  "precoLiberado": "N\u00e3o",
  [...]
}
```

Os dados então podem gerar funcionalidades práticas e úteis!

### Requisições com múltiplos parâmetros

Muitos dos *endpoints* abertos disponíveis na Nuvem Cívica permitem uma busca mais parametrizada por meio de atributos específicos. Utilizando agora a base de Escolas e a seguinte requisição como exemplo:

 > **GET** - `http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/`
 > [(Ver documentação)](https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EscolasAPI.md#buscar-escolas)

Em buscas genéricas, parâmetros são necessários para filtrar os resultados retornados por essas pesquisas. Estes parâmetros são inseridos na busca por meio da sintaxe ` "...rest/escolas?tipoparam1=param1&tipoparam2=param2"`. Os tipos de parâmetros disponíveis podem ser encontrados na [documentação](https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EscolasAPI.md) dos *endpoints.*

#### Requisição
Numa situação onde fosse necessário pesquisar todas as **escolas** **particulares** **em atividade do DF**, a seguinte chamada deve ser feita:

> **GET** http://mobile-aceite.tcu.gov.br:80/nossaEscolaRS/rest/escolas?rede=Privada&uf=df&situacaoFuncionamento=Em%20Atividade&quantidadeDeItens=20

#### Retorno 

Após executada esta chamada, serão retornadas as escolas que correspondem aos requisitos solicitados. Um trecho da resposta pode ser observado abaixo:
```json
[ 
   {
    "codEscola": 53007638,
    "nome": "CR FREDERICO OZANAM",
    "rede": "Privada",
    "email": "CRECHEFREDERICOOZANAM@HOTMAIL.COM",
    "esferaAdministrativa": "Privada",
    "categoriaEscolaPrivada": "Filantrópica",
    "situacaoFuncionamento": "Em Atividade",
    "tipoConvenioPoderPublico": "Estadual",
    "cnpj": "00573550000108",
    "telefone": "61 33711868",
    "seFimLucrativo": "N",
    "seConveniadaSetorPublico": "S",
    "qtdSalasExistentes": 8,
    "qtdSalasUtilizadas": 8,
    "qtdFuncionarios": 67,
    "qtdComputadores": 11,
    "qtdComputadoresPorAluno": 0,
    "qtdAlunos": 140,
    "endereco": {
      "cep": "72215310",
      "descricao": "QNM 31 - MOD C - AE ",
      "bairro": "CEILANDIA SUL",
      "municipio": "Brasília",
      "uf": "DF"
    }, [...]
```

### Requisições georreferenciadas

Os dados da Nuvem Cívica também dispõem de informações de geolocalização e diversos outros atributos acerca de entidades de todo o Brasil. Atualmente, podem ser pesquisados:

 - **Escolas**
 - **Estabelecimentos de Saúde**
 - **Unidades de Assistência Social**
 - **Postos do SINE (empregos)**

Para ilustrar o exemplo, executaremos uma requisição de busca de escolas por meio de localização.
#### Requisição

A chamada abaixo busca dados de escolas próximas a uma coordenada de referência:
 > **GET** - `http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/latitude/{latitude}/longitude/{longitude}/raio/{raio}`
 > [(Ver documentação)](https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EscolasAPI.md#escolas-georreferenciadas)

Em que `{latitude} e {longitude}` são as coordenadas de pesquisa e `{raio}` o raio em quilômetros da área analisada pela busca.

Tomando como exemplo as coordenadas da **sede do TCU** `(latitude: -15.8039346, longitude: -47.863683)`, podemos montar a seguinte requisição para pesquisar todas as escolas num raio de 2km:

 > **GET** - http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/latitude/-15.8039346/longitude/-47.863683/raio/2

#### Retorno

Após a busca, obtemos a seguinte resposta em **JSON** (trecho):
```json
[ 
  {
    "codEscola": 53001397,
    "nome": "COL SANTA ROSA",
    "latitude": -15.807057,
    "longitude": -47.880608,
    "rede": "Privada",
    "email": "DIRECAO@CSRDF.COM.BR",
    "esferaAdministrativa": "Privada",
    "categoriaEscolaPrivada": "Particular",
    "situacaoFuncionamento": "Em Atividade",
    "tipoConvenioPoderPublico": "Estadual e Municipal",
    "cnpj": "61638227000313",
    "telefone": "61 32242966",
    "seFimLucrativo": "S",
    "seConveniadaSetorPublico": "N",
    "qtdSalasExistentes": 25,
    "qtdSalasUtilizadas": 21,
    "qtdFuncionarios": 107,
    "qtdComputadores": 55,
    "qtdComputadoresPorAluno": 26,
    "qtdAlunos": 674,
    "endereco": {
      "cep": "70200610",
      "descricao": "SGAS 601 - CJ C - LT 03 ",
      "bairro": "ASA SUL",
      "municipio": "Bras\u00edlia                                          ",
      "uf": "DF"
    },
    [...]
 ]
```

[http://mobile-aceite.tcu.gov.br/mapa-da-saude/rest/remedios]:http://mobile-aceite.tcu.gov.br/mapa-da-saude/rest/remedios
[documentação]:https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EstabelecimentosAPI.md#remédios-1
[EscolasAPI.md]:https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EscolasAPI.md
[EstabelecimentosAPI.md]:https://github.com/AppCivicoPlataforma/AppCivico/blob/master/EstabelecimentosAPI.md
[REST]:https://www.infoq.com/br/articles/rest-introduction
