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
    * rel - Diz para qual objeto o "href" é relativo.
    * href - Referência ao endpoint de encontrar escola por código, que representa onde se pode encontrar os dados dessa escola.
* codEscola -  Código único que identifica uma escola.
* nome - Nome da escola.
* latitude - Referênte à geolocalização da escola indicando a latitude.
* longitude - Referênte à geolocalização da escola indicando a longitude.
* rede - Representa a rede de ensino a qual essa escola está vinculada.
* email - E-mail da escola.
* esferaAdministrativa - Representa o tipo administrativo do estabelecimento, por exemplo, se é de esfera estadual, municipal, empresa privada, entre outros.
* categoriaEscolaPrivada - Se a escola pertencer a rede privada, indica a categoria da escola privada.
* situacaoFuncionamento - Indica qual a atual situação de funcionamento da escola.
* seFimLucrativo - Indica se a escola possui fins lucrativos.
* seConveniadaSetorPublico - Indica se a escola é conveniada à algun setor público.
* qtdSalasExistentes - Indica a quantidade total de salas no espaço da escola.
* qtdSalasUtilizadas - Indica a quantidade de salas utilizadas no espaço da escola.
* qtdFuncionarios - Indica a quantidade total de funcionarios que trabalham na escola.
* qtdComputadores - Indica a quantidade total de computadores na escola.
* qtdComputadoresPorAluno - 
* qtdAlunos - Indica a quantidade total de alunos atualmente matriculados na escola.
* endereco 
    * cep - Cep da escola
    * descricao - Descrição ou logradouro do endereço.
    * bairro - Bairro onde se localiza a escola.
    * municipio - Município onde se localiza a escola.                                  ",
    * uf - Estado onde se localiza a escola.

* zona - Indica se a escola é de zona urbana ou rural.
* infraestrutura 
    * temQuadraEsporteCoberta - Indica se a escola possui quadra de esporte coberta.
    * temQuadraEsporteDescoberta - Indica se a escola possui quadra de esporte descoberta.
    * temInternet - Indica se a escola possui internet.
    * temBandaLarga - Indica se a escola possui banda larga.
    * temLaboratorioInformatica - Indica se a escola possui laboratório de informática.
    * temLaboratorioCiencias - Indica se a escola possui laboratório de ciências.
    * temRefeitorio - Indica se a escola possui refeitório.
    * temAuditorio - Indica se a escola possui auditório.
    * temDespensa - Indica se a escola possui despensa.
    * temAlmoxarifado - Indica se a escola possui almoxarifado.
    * temPatioCoberto - Indica se a escola possui pátio coberto.
    * temPatioDescoberto - Indica se a escola possui pátio descoberto.
    * temParqueInfantil - Indica se a escola possui parque infantil.
    * temCozinha - Indica se a escola possui cozinha.
    * temBiblioteca - Indica se a escola possui biblioteca.
    * temBercario - Indica se a escola possui berçario.
    * temSanitarioNoPredio - Indica se a escola possui sanitário no prédio.
    * temSanitarioForaPredio - Indica se a escola possui sanitário fora do prédio.
    * temSalaLeitura - Indica se a escola possui sala de leitura.
    * temAreaVerde - Indica se a escola possui área verde.
    * temAguaFiltrada - Indica se a escola possui água filtrada.
    * temAcessibilidade - Indica se a escola possui acessibilidade.
    * temCreche - Indica se a escola possui creche.
    * temEnsinoFundamental - Indica se a escola possui ensino fundamental.
    * temEnsinoMedio - Indica se a escola possui ensino médio.
    * temEnsinoMedioNormal - Indica se a escola possui ensino médio normal.
    * temEnsinoMedioProfissional - Indica se a escola possui ensino médio profissional.
    * temEnsinoMedioIntegrado - Indica se a escola possui ensino médio integrado.
    * temEducacaoJovemAdulto - Indica se a escola possui educação jovem adulto.
    * temEducacaoIndigena - Indica se a escola possui educação indígena.
    * banheiroTemChuveiro - Indica se a escola possui chuveiro.
    * ofereceAlimentacao - Indica se a escola oferece alimentação.
    * atendeEducacaoEspecializada - Indica se a escola possui atendimento à educação especial.

