#Estabelecimentos de Saúde
##API Referece
Esses *endpoints* são responsáveis por fornecer dados sobre os estabelecimentos de Saúde.
##Fonte
[DataSUS - Cadastro Nacional de Estabelecimentos de Saúde(CNES)](http://cnes.datasus.gov.br/)

## URL Base 
[http://mobile-aceite.tcu.gov.br/mapa-da-saude/](http://mobile-aceite.tcu.gov.br:80/mapa-da-saude/)

Clique aqui para testar os endpoints no [Swagger API](http://mobile-aceite.tcu.gov.br/appCivicoRS/swagger/index.html?url=/mapa-da-saude/v2/api-docs) 

## Docs
* [/rest/estabelecimentos/latitude/{latitude}/longitude/{longitude}/raio/{raio}](#Estabelecimentos)





###Estabelecimentos
* /rest/estabelecimentos/latitude/{latitude}/longitude/{longitude}/raio/{raio}

    Busca estabelecimentos de sáude ao redor de uma coordenada geográfica com determinado raio de distância.
    **Parâmetros**
  * {latitude} - Parâmetro de path que representa a latitude do ponto de referência para a busca.
  * {longitude} - Parâmetro de path que representa a longitude do ponto de referência para a busca.
  * {raio} - Parâmetro de path que representa a distância, a partir do ponto de referência, que serão buscados os estabelecimentos.
  * texto - Parâmetro de query que é utilizado para busca textual livre em cima de diversos dados relativos a estabelecimentos, como por exemplo, especialidades, serviços e profissionais.
  * categoria - Parâmetro de query utilizado para filtrar os estabelecimentos de saúdes por categorias específicas. As categorias possíveis para filtro são:
      * HOSPITAL 
      * POSTO DE SAÚDE 
      * URGÊNCIA 
      * SAMU 
      * FARMÁCIA 
      * CLÍNICA  
      * CONSULTÓRIO 
      * LABORATÓRIO 
      * APOIO À SAÚDE 
      * ATENÇÃO ESPECÍFICA 
      * UNIDADE ADMINISTRATIVA 
      * ATENDIMENTO DOMICILIAR 
    Observação: O valor para filtro deve ser passado todo em maíusculo e com acentos, exatamente iguais à listagem acima.
  * campos - Representa a lista de campos a serem retornados. Caso seja omitida, todos os campos serão retornados. Os campos que podem ser retornados são: 
      * codCnes - O código único do estabelecimento no Cadastro Nacional de Estabelecimentos de Saúde(CNES).
      * codUnidade - Código único do estabelecimento de saúde, diferente do código do CNES.
      * codIbge -  Código de registro do estabelecimento no IBGE.
      * nomeFantasia -  Nome fantasia do estabelecimento de Saúde.
      * natureza - Representa a natureza empresárial do estabelecimento.
      * tipoUnidade - Representa o tipo(categoria) do estabeleciemento de saúde.
      * esferaAdministrativa - Representa o tipo administrativo do estabelecimento, por exemplo, se é de esfera estadual, municipal, empresa privada, entre outros.
      * vinculoSus - Define se o estabelecimento tem ou não vínculo com o Sistema Único de Saúde.
      * retencao - Define se o estabelecimento é uma unidade publica ou algum dos tipos de unidades privadas.
      * fluxoClientela - Representa o tipo de atendimento oferecido nesse estabelecimento.
      * origemGeografica - Representa qual a origem geográfica do estabelecimento.
      * temAtendimentoUrgencia - 
      * temAtendimentoAmbulatorial - 
      * temCentroCirurgico - 
      * temObstetra - 
      * temNeoNatal - 
      * temDialise - 
      * descricaoCompleta": "PSF 16 NOVA FORMOSA  ADMINISTRACAO DIRETA DA SAUDE (MS,SES e SMS)      SAUDE BUCAL MI ABORDAGEM  FUMANTE   CIRURGIAO-DENTISTA DA ESTRATEGIA DE SAUDE DA  MEDICO DA ESTRATEGIA DE SAUDE DA  ENFERMEIRO DA ESTRATEGIA DE SAUDE DA  ",
      * "tipoUnidadeCnes": "CENTRO DE SAUDE/UNIDADE BASICA",
      * "categoriaUnidade": "POSTO DE SAÚDE",
      * "logradouro": "RUA 205",
      * "numero": "S/N",
      * "bairro": "NOVA FORMOSA",
      * "cidade": "FORMOSA",
      * "uf": "GO",
      * "cep": "73809330",
      * "turnoAtendimento": "Atendimento nos turnos da manhã e à tarde.",
      * "lat": -15.5232632160182,
      * "long": -47.3129868507372
  * quantidade - Parâmetro de query define a quantidade máxima de estabelecimentos a serem retornados. Caso não seja informado, utiliza valor padrão igual a 30.

