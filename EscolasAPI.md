#Escolas
##API Referece
Esses *endpoints* são responsáveis por fornecer dados sobre escolas públicas e privadas do país.
##Fonte
[Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira (INEP)](http://portal.inep.gov.br/)

## URL Base 
[http://mobile-aceite.tcu.gov.br:80/nossaEscolaRS/](http://mobile-aceite.tcu.gov.br:80/nossaEscolaRS/)

Clique aqui para testar os endpoints no [Swagger API](http://mobile-aceite.tcu.gov.br/appCivicoRS/swagger/index.html?url=/nossaEscolaRS/v2/api-docs) 

## Docs
* [`GET - rest/escolas`](#escolas)
* [`GET - /rest/escolas/{codEscola}`](#encontrar-escolas)
* [`GET - /rest/escolas/{codEscola}/avaliacoes`](#avaliacoes-da-escola)


## Dados disponíveis
Cada escola está representado pelos seguintes dados.
* links - Conjunto de links refêrentes à escola.
    * rel - 
    * href - http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364

* codEscola - 
* nome - 
* latitude - 
* longitude - 
* rede - 
* email - 
* esferaAdministrativa - 
* categoriaEscolaPrivada -
* situacaoFuncionamento - 
* seFimLucrativo - 
* seConveniadaSetorPublico - 
* qtdSalasExistentes - 
* qtdSalasUtilizadas - 
* qtdFuncionarios - 
* qtdComputadores - 
* qtdComputadoresPorAluno - 
* qtdAlunos - 
* endereco -
    * cep": "76820247",
    * descricao": "RUA RAIMUNDO CANTUARIA 5129",
    * bairro": "AGENOR DE CARVALHO",
    * municipio": "Porto Velho                                       ",
    * uf": "RO"

* zona - "URBANA",
* infraestrutura - 
    * temQuadraEsporteCoberta": "S",
    * temQuadraEsporteDescoberta": "N",
    * temInternet": "S",
    * temBandaLarga": "S",
    * temLaboratorioInformatica": "S",
    * temLaboratorioCiencias": "N",
    * temRefeitorio": "S",
    * temAuditorio": "N",
    * temDespensa": "N",
    * temAlmoxarifado": "N",
    * temPatioCoberto": "S",
    * temPatioDescoberto": "N",
    * temParqueInfantil": "N",
    * temCozinha": "S",
    * temBiblioteca": "S",
    * temBercario": "N",
    * temSanitarioNoPredio": "S",
    * temSanitarioForaPredio": "N",
    * temSalaLeitura": "S",
    * temAreaVerde": "S",
    * temAguaFiltrada": "S",
    * temAcessibilidade": "S",
    * temCreche": "N",
    * temEnsinoFundamental": "S",
    * temEnsinoMedio": "N",
    * temEnsinoMedioNormal": "N",
    * temEnsinoMedioProfissional": "N",
    * temEnsinoMedioIntegrado": "N",
    * temEducacaoJovemAdulto": "S",
    * temEducacaoIndigena": "N",
    * banheiroTemChuveiro": "S",
    * ofereceAlimentacao": "S",
    * atendeEducacaoEspecializada": "S"

