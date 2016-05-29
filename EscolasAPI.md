#Escolas
##API Referece
Esses *endpoints* são responsáveis por fornecer dados sobre escolas públicas e privadas do país.
##Fonte
[Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira (INEP)](http://portal.inep.gov.br/)

## URL Base 
`http://mobile-aceite.tcu.gov.br:80/nossaEscolaRS/`

Clique aqui para testar os endpoints no [Swagger API](http://mobile-aceite.tcu.gov.br/appCivicoRS/swagger/index.html?url=/nossaEscolaRS/v2/api-docs) 

## Docs
* [`GET - rest/escolas`](#escolas)
* [`GET - /rest/escolas/{codEscola}`](#encontrar-escola)
* [`GET - /rest/escolas/{codEscola}/avaliacoes`](#avaliações-de-escola)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}`](#avaliações-de-escola-por-ano)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/media`](#média-de-avaliações-de-escola-por-ano)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/tipo/{tipo}`](#avaliações-de-escola-por-ano-e-tipo)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/tipo/{tipo}/media`](#média-de-avaliações-de-escola-por-ano-e-tipo)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/media`](#média-de-avaliações-de-escola)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/tipo/{tipo}`](#avaliações-de-escola-por-tipo)
* [`GET - /rest/escolas/{codEscola}/avaliacoes/tipo/{tipo}/media`](#média-de-avaliações-de-escola-por-tipo)
* [`GET - /rest/tiposavaliacao`](#tipos-de-avaliação)

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
* qtdComputadoresPorAluno - Indica a quantidade de computadores por aluno.
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

###Escolas

  * `GET - rest/escolas`
  
      Busca dados de escolas próximas à uma coordenada de referência possibilitando também uma busca por nome.

   **Parâmetros**
   
      * nome - Parâmetro de query opcional que pode ser completo ou parte do nome para busca.
      * latitude - Parâmetro de query que recebe a latitude para busca georeferênciada.
      * longitude - Parâmetro de query que recebe a longitude para busca georeferênciada.
      * raio - Parâmetro de query que recebe o limite em quilometros a partir das coordenadas de referência que as  escolas serão buscadas.
      * pagina - Parâmetro de query opcional para uma busca paginada, número da página com valor padrão 0.
      * quantidadeDeItens -  Parâmetro de query opcional que define o máximo de escolas retornadas na busca. Valor padrão é 20.
      
   **Retorno**
      
      * 400 - Combinação inválida de parâmetros. As combinações válidas são: nenhum parâmetro OU (nome) OU (latitude, longitude, raio). 
      * 200 - Ok
      
         **Exemplo**
         
         ````
            [
               {
                "links": [
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001399"
                  }
                ],
                "codEscola": 11001399,
                "nome": "EMEF LEOCADIO PARDO",
                "rede": "Pública",
                "email": "NESC.SEMED@GMAIL.COM",
                "esferaAdministrativa": "Municipal",
                "categoriaEscolaPrivada": "Não é privada",
                "situacaoFuncionamento": "Em Atividade",
                "seFimLucrativo": "N",
                "seConveniadaSetorPublico": "N",
                "qtdSalasExistentes": 3,
                "qtdSalasUtilizadas": 2,
                "qtdFuncionarios": 4,
                "qtdComputadores": 0,
                "qtdComputadoresPorAluno": 0,
                "qtdAlunos": 26,
                "endereco": {
                  "cep": "76801000",
                  "descricao": "TERRA CAIDA BAIXO MADEIRA S/NSAO CARLOS",
                  "bairro": "ZONA RURAL",
                  "municipio": "Porto Velho                                       ",
                  "uf": "RO"
                },
                "zona": "RURAL",
                "infraestrutura": {
                  "temQuadraEsporteCoberta": "N",
                  "temQuadraEsporteDescoberta": "N",
                  "temInternet": "N",
                  "temBandaLarga": "N",
                  "temLaboratorioInformatica": "N",
                  "temLaboratorioCiencias": "N",
                  "temRefeitorio": "S",
                  "temAuditorio": "N",
                  "temDespensa": "S",
                  "temAlmoxarifado": "N",
                  "temPatioCoberto": "N",
                  "temPatioDescoberto": "N",
                  "temParqueInfantil": "N",
                  "temCozinha": "S",
                  "temBiblioteca": "N",
                  "temBercario": "N",
                  "temSanitarioNoPredio": "S",
                  "temSanitarioForaPredio": "N",
                  "temSalaLeitura": "N",
                  "temAreaVerde": "S",
                  "temAguaFiltrada": "S",
                  "temAcessibilidade": "N",
                  "temCreche": "N",
                  "temEnsinoFundamental": "S",
                  "temEnsinoMedio": "N",
                  "temEnsinoMedioNormal": "N",
                  "temEnsinoMedioProfissional": "N",
                  "temEnsinoMedioIntegrado": "N",
                  "temEducacaoJovemAdulto": "N",
                  "temEducacaoIndigena": "N",
                  "banheiroTemChuveiro": "N",
                  "ofereceAlimentacao": "S",
                  "atendeEducacaoEspecializada": "N"
                }
              }
            ]
         ```
         
### Encontrar escola

  * `GET - /rest/escolas/{codEscola}`
      
      Busca dados de uma escola a partir do se código identificação único.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
         
         ```
            [
               {
                "links": [
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001399"
                  }
                ],
                "codEscola": 11001399,
                "nome": "EMEF LEOCADIO PARDO",
                "rede": "Pública",
                "email": "NESC.SEMED@GMAIL.COM",
                "esferaAdministrativa": "Municipal",
                "categoriaEscolaPrivada": "Não é privada",
                "situacaoFuncionamento": "Em Atividade",
                "seFimLucrativo": "N",
                "seConveniadaSetorPublico": "N",
                "qtdSalasExistentes": 3,
                "qtdSalasUtilizadas": 2,
                "qtdFuncionarios": 4,
                "qtdComputadores": 0,
                "qtdComputadoresPorAluno": 0,
                "qtdAlunos": 26,
                "endereco": {
                  "cep": "76801000",
                  "descricao": "TERRA CAIDA BAIXO MADEIRA S/NSAO CARLOS",
                  "bairro": "ZONA RURAL",
                  "municipio": "Porto Velho                                       ",
                  "uf": "RO"
                },
                "zona": "RURAL",
                "infraestrutura": {
                  "temQuadraEsporteCoberta": "N",
                  "temQuadraEsporteDescoberta": "N",
                  "temInternet": "N",
                  "temBandaLarga": "N",
                  "temLaboratorioInformatica": "N",
                  "temLaboratorioCiencias": "N",
                  "temRefeitorio": "S",
                  "temAuditorio": "N",
                  "temDespensa": "S",
                  "temAlmoxarifado": "N",
                  "temPatioCoberto": "N",
                  "temPatioDescoberto": "N",
                  "temParqueInfantil": "N",
                  "temCozinha": "S",
                  "temBiblioteca": "N",
                  "temBercario": "N",
                  "temSanitarioNoPredio": "S",
                  "temSanitarioForaPredio": "N",
                  "temSalaLeitura": "N",
                  "temAreaVerde": "S",
                  "temAguaFiltrada": "S",
                  "temAcessibilidade": "N",
                  "temCreche": "N",
                  "temEnsinoFundamental": "S",
                  "temEnsinoMedio": "N",
                  "temEnsinoMedioNormal": "N",
                  "temEnsinoMedioProfissional": "N",
                  "temEnsinoMedioIntegrado": "N",
                  "temEducacaoJovemAdulto": "N",
                  "temEducacaoIndigena": "N",
                  "banheiroTemChuveiro": "N",
                  "ofereceAlimentacao": "S",
                  "atendeEducacaoEspecializada": "N"
                }
              }
            ]
         ```
         
### Avaliações de Escola

   * `GET - /rest/escolas/{codEscola}/avaliacoes`
   
      Busca avaliações do Índice de Desenvolvimento da Educação Básica (Ideb) feitas na escola.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * pagina - Parâmetro de query opcional para uma busca paginada, número da página com valor padrão 0.
      * quantidadeDeItens -  Parâmetro de query opcional que define o máximo de escolas retornadas na busca. Valor padrão é 20.
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            {
               [ 
                "links": [
                  {
                    "rel": "escola",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364"
                  },
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364/avaliacoes/ano/2005/tipo/1"
                  }
                ],
                "tipoAvaliacao": {
                  "cod": 1,
                  "nome": "IDEB Anos Iniciais"
                },
                "ano": 2005,
                "valor": 3.4
              }
            ]
         ```
         
### Avaliações de Escola por Ano

   * `GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}`
   
      Busca avaliações do Índice de Desenvolvimento da Educação Básica (Ideb) feitas na escola por **ano**.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * {ano} - Parâmetro de path que representa o ano à ser buscado.
      * pagina - Parâmetro de query opcional para uma busca paginada, número da página com valor padrão 0.
      * quantidadeDeItens -  Parâmetro de query opcional que define o máximo de escolas retornadas na busca. Valor padrão é 20.
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            [
               {
                [ 
                "links": [
                  {
                    "rel": "escola",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364"
                  },
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364/avaliacoes/ano/2005/tipo/1"
                  }
                ],
                "tipoAvaliacao": {
                  "cod": 1,
                  "nome": "IDEB Anos Iniciais"
                },
                "ano": 2005,
                "valor": 3.4
              }
            ]
         ```
         
### Média de avaliações de Escola por Ano

   * `GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/media`
   
      Busca média de todas as avaliações feitas feitas na escola por **ano**.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * {ano} - Parâmetro de path que representa o ano à ser buscado.
      
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            {
               "media": 3.7
            }
         ```
         
### Avaliações de Escola por Ano e tipo

   * `GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/tipo/{tipo}`
   
      Busca avaliações do Índice de Desenvolvimento da Educação Básica (Ideb) feitas na escola por **ano** e **tipo**.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * {ano} - Parâmetro de path que representa o ano à ser buscado.
      * {tipo} - Parâmetro de path qua representa o código do tipo de avaliação a ser buscada.
      
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            [
               {
                [ 
                "links": [
                  {
                    "rel": "escola",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364"
                  },
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364/avaliacoes/ano/2005/tipo/1"
                  }
                ],
                "tipoAvaliacao": {
                  "cod": 1,
                  "nome": "IDEB Anos Iniciais"
                },
                "ano": 2005,
                "valor": 3.4
              }
            ]
         ```         
         
         
### Média de avaliações de Escola por Ano e tipo

   * `GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/tipo/{tipo}/media`
   
      Busca média de todas as avaliações feitas na escola por **ano** e **tipo**.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * {ano} - Parâmetro de path que representa o ano à ser buscado.
      * {tipo} - Parâmetro de path qua representa o código do tipo de avaliação a ser buscada.
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            {
               "media": 3.7
            }
         ```
         
### Média de avaliações de Escola

   * `GET - /rest/escolas/{codEscola}/avaliacoes/media`
   
      Busca média de todas as avaliações feitas na escola.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            {
               "media": 3.7
            }
         ```
         
### Avaliações de Escola por tipo

   * `GET - /rest/escolas/{codEscola}/avaliacoes/ano/{ano}/tipo/{tipo}`
   
      Busca avaliações do Índice de Desenvolvimento da Educação Básica (Ideb) feitas na escola por **tipo**.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * {tipo} - Parâmetro de path qua representa o código do tipo de avaliação a ser buscada.
      * pagina - Parâmetro de query opcional para uma busca paginada, número da página com valor padrão 0.
      * quantidadeDeItens -  Parâmetro de query opcional que define o máximo de escolas retornadas na busca. Valor padrão é 20.
      
   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
         
         ```
            [
               {
                [ 
                "links": [
                  {
                    "rel": "escola",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364"
                  },
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/nossaEscolaRS/rest/escolas/11001364/avaliacoes/ano/2005/tipo/1"
                  }
                ],
                "tipoAvaliacao": {
                  "cod": 1,
                  "nome": "IDEB Anos Iniciais"
                },
                "ano": 2005,
                "valor": 3.4
              }
            ]
         ```            

### Média de avaliações de Escola por tipo

   * `GET - /rest/escolas/{codEscola}/avaliacoes/tipo/{tipo}/media`
   
      Busca média de todas as avaliações feitas na escola por **tipo**.

   **Parâmetros**
   
      * {codEscola} - Parâmetro de path que representa o código a ser buscado.
      * {tipo} - Parâmetro de path qua representa o código do tipo de avaliação a ser buscada.

   **Retorno**
      
      * 404 - Escola com o código passado como parâmetro não foi encontrada.
      * 200 - Ok
         
         **Exemplo**
            
         ```
            {
               "media": 3.7
            }
         ```

## Tipos de Avaliação

   * `GET /rest/tiposavaliacao`
   
      Busca todos os tipos de avaliações disponíveis.
   
   **Parâmetros**
      
      Não há parâmetros.

   **Retorno**
      
      * 200 - OK
      
         **Exemplo**
            
         ```
            {
               "cod": 2,
               "nome": "IDEB Anos Finais"
            }
         ```
        
