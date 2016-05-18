#Estabelecimentos de Saúde
##API Referece
Esses *endpoints* são responsáveis por fornecer dados sobre os estabelecimentos de Saúde.
##Fonte
[DataSUS - Cadastro Nacional de Estabelecimentos de Saúde(CNES)](http://cnes.datasus.gov.br/)

## URL Base 
[http://mobile-aceite.tcu.gov.br/mapa-da-saude/](http://mobile-aceite.tcu.gov.br:80/mapa-da-saude/)

Clique aqui para testar os endpoints no [Swagger API](http://mobile-aceite.tcu.gov.br/appCivicoRS/swagger/index.html?url=/mapa-da-saude/v2/api-docs) 

## Docs
* [`/rest/estabelecimentos/latitude/{latitude}/longitude/{longitude}/raio/{raio}`](#estabelecimento)
* [`/rest/estabelecimentos/unidade/{codUnidade}`](#detalhes)

## Dados disponíveis
Cada estabelecimento de saúde está representado pelos seguintes dados.
* codCnes - O código único do estabelecimento no Cadastro Nacional de Estabelecimentos de Saúde(CNES).
* codUnidade - Código único do estabelecimento de saúde, diferente do código do CNES.
* codIbge -  Código de registro do estabelecimento no IBGE.
* nomeFantasia -  Nome fantasia do estabelecimento de Saúde.
* natureza - Representa a natureza empresárial do estabelecimento.
* tipoUnidade - Representa o tipo do estabeleciemento.
* esferaAdministrativa - Representa o tipo administrativo do estabelecimento, por exemplo, se é de esfera estadual, municipal, empresa privada, entre outros.
* vinculoSus - Define se o estabelecimento tem ou não vínculo com o Sistema Único de Saúde.
* retencao - Define se o estabelecimento é uma unidade publica ou algum dos tipos de unidades privadas.
* fluxoClientela - Representa o tipo de atendimento oferecido nesse estabelecimento.
* origemGeografica - Representa qual a origem geográfica do estabelecimento.
* temAtendimentoUrgencia - Define se o estabelecimento tem ou não atendimento de urgência.
* temAtendimentoAmbulatorial - Define se o estabelecimento tem ou não atendimento ambulantórial.
* temCentroCirurgico - Define se o estabelecimento tem ou não centro cirúrgico.
* temObstetra - Define se o estabelecimento tem ou não obestetra.
* temNeoNatal - Define se o estabelecimento tem ou não atendimento neo natal.
* temDialise - Define se o estabelecimento tem ou não diálise.
* descricaoCompleta - Descrição do estabelecimento.
* tipoUnidadeCnes - Descreve o tipo de estabelecimento de acordo com o CNES.
* categoriaUnidade - Representa o tipo do estabeleciemento.
* logradouro - Referente ao endereço do estabelecimento e representa o logradouro.
* numero - Referente ao endereço do estabelecimento e representa o número.
* bairro - Referente ao endereço do estabelecimento e representa o bairro.
* cidade - Referente ao endereço do estabelecimento e representa a cidade.
* uf - Referente ao endereço do estabelecimento e representa a uf.
* cep -  Referente ao endereço do estabelecimento e representa o CEP.
* turnoAtendimento -  Referente aos turnos de atendimento do estabelecimento.
* lat - Referênte à geolocalização do estabelecimento indicando latitude.
* long - Referênte à geolocalização do estabelecimento indicando latitude.


###Estabelecimentos

* `/rest/estabelecimentos/latitude/{latitude}/longitude/{longitude}/raio/{raio}`

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
    **Observação:** O valor para filtro deve ser passado todo em maíusculo e com acentos, exatamente iguais à listagem acima.
  * campos - Representa a lista de campos a serem retornados. Caso seja omitida, todos os campos serão retornados. Os campos que podem ser retornados são: 
       codCnes, codUnidade, codIbge, nomeFantasia, natureza, tipoUnidade, esferaAdministrativa, vinculoSus, retencao, fluxoClientela, origemGeografica, temAtendimentoUrgencia, temAtendimentoAmbulatorial, temCentroCirurgico,temObstetra,temNeoNatal, temDialise, descricaoCompleta,tipoUnidadeCnes, categoriaUnidade, logradouro, numero, bairro, cidade, uf, cep, turnoAtendimento, lat, long.
    **Observações:** Os campos devem ser passados separados por vígurla e sem espaços em branco. 
    
    Para referência do significado de cada campo veja na sessão de `Dados disponíveis` topo do documento.
  * quantidade - Parâmetro de query define a quantidade máxima de estabelecimentos a serem retornados. Caso não seja informado, utiliza valor padrão igual a 30.

    **Retorno**
    
    **Exemplo**
    ````
        [
            {
                "codCnes": 5168945,
                "codUnidade": "5208005168945",
                "codIbge": 520800,
                "nomeFantasia": "ODONTOLOGICA",
                "natureza": "Empresa",
                "tipoUnidade": "CONSULTÓRIO PARTICULAR",
                "esferaAdministrativa": "Privada",
                "vinculoSus": "Não",
                "retencao": "Unidade Privada Lucrativa***",
                "fluxoClientela": "Atendimento de demanda espontânea e referenciada",
                "origemGeografica": "CNES_GEO",
                "temAtendimentoUrgencia": "Não",
                "temAtendimentoAmbulatorial": "Sim",
                "temCentroCirurgico": "Não",
                "temObstetra": "Não",
                "temNeoNatal": "Não",
                "temDialise": "Sim",
                "descricaoCompleta": "ODONTOLOGICA  EMPRESA PRIVADA     CIRURGIAO DENTISTA - CLINICO GERAL  ",
                "tipoUnidadeCnes": "CONSULTORIO ISOLADO",
                "categoriaUnidade": "CONSULTÓRIO",
                "logradouro": "R STA LUZIA",
                "numero": "181",
                "bairro": "CENTRO",
                "cidade": "FORMOSA",
                "uf": "GO",
                "cep": "73801440",
                "telefone": "06136314461",
                "turnoAtendimento": "Atendimento nos turnos da manhã e à tarde.",
                "lat": -15.53375,
                "long": -47.32255
            }
        ]    
    ```
    
    Para referência do significado de cada campo veja na sessão de `Dados disponíveis` topo do documento.
    
* `/rest/estabelecimentos/unidade/{codUnidade}`

    Busca dados de um estabelecimento de saúde pelo campo único de código unidade.
    **Parâmetros**
    * {codUnidade} - Parâmetro de path que indica o código de unidade.
    
    **Retorno**
    
    **Exemplo**
    ````
        [
            {
                "codCnes": 5168945,
                "codUnidade": "5208005168945",
                "codIbge": 520800,
                "nomeFantasia": "ODONTOLOGICA",
                "natureza": "Empresa",
                "tipoUnidade": "CONSULTÓRIO PARTICULAR",
                "esferaAdministrativa": "Privada",
                "vinculoSus": "Não",
                "retencao": "Unidade Privada Lucrativa***",
                "fluxoClientela": "Atendimento de demanda espontânea e referenciada",
                "origemGeografica": "CNES_GEO",
                "temAtendimentoUrgencia": "Não",
                "temAtendimentoAmbulatorial": "Sim",
                "temCentroCirurgico": "Não",
                "temObstetra": "Não",
                "temNeoNatal": "Não",
                "temDialise": "Sim",
                "descricaoCompleta": "ODONTOLOGICA  EMPRESA PRIVADA     CIRURGIAO DENTISTA - CLINICO GERAL  ",
                "tipoUnidadeCnes": "CONSULTORIO ISOLADO",
                "categoriaUnidade": "CONSULTÓRIO",
                "logradouro": "R STA LUZIA",
                "numero": "181",
                "bairro": "CENTRO",
                "cidade": "FORMOSA",
                "uf": "GO",
                "cep": "73801440",
                "telefone": "06136314461",
                "turnoAtendimento": "Atendimento nos turnos da manhã e à tarde.",
                "lat": -15.53375,
                "long": -47.32255
            }
        ]    
    ```
    
    Para referência do significado de cada campo veja na sessão de `Dados disponíveis` topo do documento.
    
* 

    
