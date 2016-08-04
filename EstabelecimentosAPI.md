#Estabelecimentos de Saúde
##API Referece
Esses *endpoints* são responsáveis por fornecer dados sobre os estabelecimentos de Saúde.
##Fonte
[DataSUS - Cadastro Nacional de Estabelecimentos de Saúde(CNES)](http://cnes.datasus.gov.br/)

## URL Base 
[http://mobile-aceite.tcu.gov.br/mapa-da-saude/](http://mobile-aceite.tcu.gov.br:80/mapa-da-saude/)

Clique aqui para testar os endpoints no [Swagger API](http://mobile-aceite.tcu.gov.br/appCivicoRS/swagger/index.html?url=/mapa-da-saude/v2/api-docs) 

## Docs
* [`GET - /rest/estabelecimentos/latitude/{latitude}/longitude/{longitude}/raio/{raio}`](#estabelecimentos)
* [`GET - /rest/estabelecimentos/unidade/{codUnidade}`](#encontrar-estabelecimento)
* [`GET - /rest/especialidades/unidade/{codUnidade}`](#especialidades)
* [`GET - /rest/profissionais/unidade/{codUnidade}`](#profissionais)
* [`GET - /rest/servicos/unidade/{codUnidade}`](#serviços-especializados)

### Remédios
* [`GET - /rest/remedios`](#remédios)

### Assistência Social

* [`GET - /rest/assistenciasocial/cras`](#cras-por-município)
* [`GET- /rest/assistenciasocial/cras/id/{idCras}`](#cras-por-código)
* [`GET- /rest/assistenciasocial/cras/latitude/{latitude}/longitude/{longitude}/raio/{raio}`]()
* [`GET- /rest/assistenciasocial/creas`]()
* [`GET- /rest/assistenciasocial/creas/id/{idCreas}`]()
* [`GET- /rest/assistenciasocial/creas/latitude/{latitude}/longitude/{longitude}/raio/{raio}`]()


### Empregos

* [`GET- /rest/emprego`]()
* [`GET- /rest/emprego/cod/{codPosto}`]()
* [`GET- /rest/emprego/latitude/{latitude}/longitude/{longitude}/raio/{raio}`]()

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


### Estabelecimentos

* `GET - /rest/estabelecimentos/latitude/{latitude}/longitude/{longitude}/raio/{raio}`

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
    
    Para referência do significado de cada campo veja na sessão de [`Dados disponíveis`](#dados-disponíveis) topo do documento.
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
    
    Para referência do significado de cada campo veja na sessão de [`Dados disponíveis`](#dados-disponíveis) topo do documento.
    
### Encontrar estabelecimento

* `GET - /rest/estabelecimentos/unidade/{codUnidade}`

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
    
    Para referência do significado de cada campo veja na sessão de [`Dados disponíveis`](#dados-disponíveis) topo do documento.
    
### Especialidades

* `GET - /rest/especialidades/unidade/{codUnidade}`
    
    Busca especialidades disponíveis em um estabelecimento de saúde identificado pelo código unidade.
    
    **Parâmetros**
    
    * {codUnidade} - Parâmetro de path que indica o código de unidade.
    
    **Retorno**
    
    **Exemplo**
    ```
        [
          {
            "descricaoHabilitacao": "ATENCAO A SAUDE BUCAL",
            "descricaoGrupo": "CENTRO DE ESPECIALIDADES ODONTOLOGICAS II"
          },
          {
            "descricaoHabilitacao": "ATENCAO A SAUDE OCULAR",
            "descricaoGrupo": "PROJETO OLHAR BRASIL"
          }
        ]
    ```
    
    **Dados retornados**
    * descricaoHabilitacao - Descrição da especialidade.
    * descricaoGrupo - Grupo que a especialidade pertence.
        
### Profissionais
* `GET - /rest/profissionais/unidade/{codUnidade}`
    
    Busca tipos de profissionais disponíveis em um estabelecimento de saúde identificado pelo código unidade.

    **Parâmetros**
    
    * {codUnidade} - Parâmetro de path que indica o código de unidade.
    
    **Retorno**
    
    **Exemplo**
    ```
       [
            {
                "descricaoAtividadeProfissional": "ADMINISTRADOR ",
                "quantidadeProfissionais": 7
            },
            {
                "descricaoAtividadeProfissional": "AGENTE COMUNITARIO DE SAUDE ",
                "quantidadeProfissionais": 15
            }
        ]
    ```
    
    
    **Dados retornados**
        
    * descricaoAtividadeProfissional - Descrição da atividade profissional disponível.
    * quantidadeProfissionais - Quantidade de profissionais que atual nessa àrea no estabelecimento.
        
### Serviços especializados

* `GET - /rest/servicos/unidade/{codUnidade}` 
    
    Busca serviços especializados disponíveis em um estabelecimento de saúde identificado pelo código unidade.

    **Parâmetros**
    
    * {codUnidade} - Parâmetro de path que indica o código de unidade.
    
    **Retorno**
    
    **Exemplo**
    ````
       [
          {
            "descricaoClassificacaoServico": "SERVICO DE ATENCAO A DSTHIVAIDS",
            "descricao": "SERVICO DE ATENCAO ESPECIALIZADA - SAE"
          },
          {
            "descricaoClassificacaoServico": "SERVICO DE ATENCAO A SAUDE AUDITIVA",
            "descricao": "DIAGNOSTICO EM AUDIOLOGIA"
          }
        ]
    ```
    
    
    **Dados retornados**
        
    * descricaoClassificacaoServico - Representa a classificação do serviço especializado.
    * descricao - Descrição do serviço especializado.

### Remédios
* `GET - /rest/remedios`
    
    Pesquisa dados de medicamentos fabricados no Brasil e registrados pela ANVISA.

     **Parâmetros**
    
    * produto - Parâmetro de query que realiza busca pelo nome do produto.
    * codBarraEan - Parâmetro de query que realiza busca pelo [código de barras EAN-13](http://www.mgitech.com.br/blog/bid/112017/O-que-o-c-digo-de-barras-EAN-13), que é um código representado por 13 dígitos.
    * apresentacao - Parâmetro de query que realiza busca pela descrição do remédio.
    * quantidade - Parâmetro de query que indica quantidade máxima de remédios a serem retornados. Caso não seja informado, utiliza valor padrão igual a 30.
    
    **Retorno**
    
    **Exemplo**
    
    ```
        [
            {
                "codBarraEan": "7891058006402",
                "principioAtivo": "LEVOTIROXINA SÓDICA",
                "cnpj": "02.685.377/0001-57",
                "laboratorio": "SANOFI-AVENTIS FARMACÊUTICA LTDA",
                "codGgrem": "502816901110317",
                "registro": "1130010230185",
                "produto": "PURAN T4",
                "apresentacao": "100 MCG COM CT BL AL PLAS INC X 28",
                "classeTerapeutica": "H03A0 - PREPARAÇÕES PARA TIREOIDE",
                "precoLiberado": "Não",
                "pf0": 5.72,
                "pf12": 6.5,
                "pf17": 6.89,
                "pf17Alc": 6.89,
                "pf175": 6.93,
                "pf175Alc": 6.93,
                "pf18": 6.97,
                "pf18Alc": 6.97,
                "pf20": 7.14,
                "pmc0": 7.91,
                "pmc12": 8.98,
                "pmc17": 9.52,
                "pmc17Alc": 9.52,
                "pmc175": 9.58,
                "pmc175Alc": 9.58,
                "pmc18": 9.64,
                "pmc18Alc": 9.64,
                "pmc20": 9.87,
                "restricao": "Não",
                "cap": "Não",
                "confaz87": "Sim",
                "ultimaAlteracao": "13/04/2015",
                "cod": 502816901110317
            }
        ]
    ```
    
    **Dados retornados**
        
    * cod - Representa o código único identificador do medicamento na base de dados.
    * codBarraEan - Representa o código de barras EAN-13 [código de barras EAN-13](http://www.mgitech.com.br/blog/bid/112017/O-que-o-c-digo-de-barras-EAN-13) registrado do medicamento.
    * principioAtivo - Indica o princípio ativo do medicamento.
    * cnpj - Indica o CNPJ do laboratório fabricante do medicamento.
    * laboratorio - Indica o laboratório fabricante do remédio.
    * codGgrem - Código que identifica o medicamento na  Gerência-Geral de Regulação
    Econômica e Monitoramento de Mercado (GGREM).
    * registro - Código de registro do medicamento.
    * produto - Representa o nome do medicamento.
    * apresentacao - Descrição do medicamento.
    * classeTerapeutica - Classe terapêutica do medicamento.
    * precoLiberado - Indica se o preço do medicamento é liberado ou não. O termo "liberado" significa que o medicamento está liberado dos critérios de estabelecimento ou ajuste de preço (Resolução CMED nº 5, de 9 de outubro de 2003). Apenas o Preço Fábrica encontra-se liberado, devendo o Preço Máximo ao Consumidor atender às margens previstas no art. 4º da Resolução nº 04, de 12 de março de 2015.
    * pf0 - Representa o preço Fábrica ou Preço Fabricante que é o preço praticado pelas empresas produtoras ou importadoras do produto e pelas empresas distribuidoras. O PF é o preço máximo permitido para venda a farmácias, drogarias e para entes da Administração Pública.
    * pf12 - Preço de fábrica com alíquotas de ICMS 12%.
    * pf17 - Preço de fábrica com alíquotas de ICMS 17%. 
    * pf17Alc - Preço de fábrica com alíquotas de ICMS 17% em áreas de Livre Comércio.
    * pf175 - Preço de fábrica com alíquotas de ICMS 17.5%.
    * pf175Alc - Preço de fábrica com alíquotas de ICMS 17.5% em áreas de Livre Comércio.
    * pf18 - Preço de fábrica com alíquotas de ICMS 18%.
    * pf18Alc - Preço de fábrica com alíquotas de ICMS 18% em áreas de Livre Comércio.
    * pf20 -  Preço de fábrica com alíquotas de ICMS 20%.
    * pmc0 -  Reprensenta o preço Máximo ao Consumidor, o qual é praticado pelas farmácias e Drogarias. O PMC é o preço máximo permitido para venda ao consumidor e inclui os impostos incidentes por estado. O preço Máximo ao Consumidor é o preço a ser praticado pelo comércio varejista, ou seja, farmácias e drogarias ( Orientação Interpretativa nº 02, 13/11/2006 – CMED.
    * pmc12 - Preço Máximo ao Consumidor com alíquotas de ICMS 12%.
    * pmc17 - Preço Máximo ao Consumidor com alíquotas de ICMS 17%.
    * pmc17Alc - Preço Máximo ao Consumidor com alíquotas de ICMS 17% em áreas de Livre Comércio.
    * pmc175 - Preço Máximo ao Consumidor com alíquotas de ICMS 17.5%.
    * pmc175Alc - Preço Máximo ao Consumidor com alíquotas de ICMS 17.5% em áreas de Livre Comércio.
    * pmc18 - Preço Máximo ao Consumidor com alíquotas de ICMS 18%.
    * pmc18Alc - Preço Máximo ao Consumidor com alíquotas de ICMS 18% em áreas de Livre Comércio.
    * pmc20 - Preço Máximo ao Consumidor com alíquotas de ICMS 20%.
    * restricao - Indica se o medicamento possui restrição hospitalar ou não.
    * cap - Indica se o preço do medicamento está sujeito ao [Coeficiente de Adequação de Preços – CAP](http://portal.anvisa.gov.br/wps/content/Anvisa+Portal/Anvisa/Pos+-+Comercializacao+-+Pos+-+Uso/Regulacao+de+Marcado/Assunto+de+Interesse/Compras+Publicas/Perguntas+e+Respostas+-+Compras+Publicas)
    * confaz87 - Indica se o medicamento está sujeito à isenção de ICMS pelo [CONVÊNIO ICMS 87/02](https://www.confaz.fazenda.gov.br/legislacao/convenios/2002/cv087_02)
    * ultimaAlteracao - Data da ultima alteração desses dados na base.
    
Para mais referências sobre os dados dos remédios, entre no site da [Agência Nacional de Vigilância Sanitária(ANVISA)](http://portal.anvisa.gov.br/wps/content/Anvisa+Portal/Anvisa/Pos+-+Comercializacao+-+Pos+-+Uso/Regulacao+de+Marcado/Assunto+de+Interesse/Mercado+de+Medicamentos/Listas+de+Precos+de+Medicamentos+03).


## Postos de atendimento do Centros de Referência de Assistência Social (CRAS)

O Centro de Referência de Assistência Social (Cras) é o sistema governamental responsável pela organização e oferta de serviços da Proteção Social Básica nas áreas de vulnerabilidade e risco social.

Por meio do Cras, as famílias em situação de extrema pobreza passam a ter acesso a serviços como cadastramento e acompanhamento em programas de transferência de renda. O País conta, atualmente, 7.669 unidades distribuídas pelo território nacional.

### CRAS por Município

    Busca as unidades do CRAS por município.
    
* `GET - /rest/assistenciasocial/cras` 
    
    **Parâmetros**
    
    * municipio - Parâmetro de query.**Opcional**. O nome do múnicipio que se deseja buscar as unidades.
    * campos - Parâmetros de query.**Opicional**.Representa a lista de campos a serem retornados. Caso seja omitida, todos os campos serão retornados. Os campos que podem ser retornados são: 
        
        **Observações:** Os campos devem ser passados separados por vígurla e sem espaços em branco. 
    * quantidade - Parâmetro de query define a quantidade máxima de estabelecimentos a serem retornados. Caso não seja informado, utiliza valor padrão igual a 30.
    
    **Retorno**
    
    * 200 - Sucesso
            Dados retornados com sucesso.
            
            **Exemplo**
                
                ```
                ```
             
    * 204 - Não encontrado
            
        Não há nenhuma unidade do CRAS nesse município.
            
    * 400 - Parâmetros inconsistêntes
            
        O parâmetro de campos está em formato inválido ou o idCRAS não é um valor numérico.

### CRAS por código

Buscar dados de uma unidade do CRAS por código.

* `GET- /rest/assistenciasocial/cras/id/{idCras}`

    **Parâmetros**
    
    * {idCras} - Parâmetro de query. Código da unidade que será buscado.
    * campos - Parâmetros de query.**Opicional**.Representa a lista de campos a serem retornados. Caso seja omitida, todos os campos serão retornados. Os campos que podem ser retornados são: 
        
        **Observações:** Os campos devem ser passados separados por vígurla e sem espaços em branco.     

    **Retorno**
    
        * 200 - Sucesso
            Dados retornados com sucesso.
            
            **Exemplo**
                
                ````
                ```
             
        * 404 - Não encontrado
            
            Não há nenhuma unidade do CRAS com o código buscado.
            
        * 400 - Parâmetros inconsistêntes
            
            O parâmetro de campos está em formato inválido ou o idCRAS não é um valor numérico.
            

### CRAS Georreferênciado

Traz postos do CRAS ao redor de uma latitude e longitude em um raio determindado.

* `GET- /rest/assistenciasocial/cras/latitude/{latitude}/longitude/{longitude}/raio/{raio}`

    **Parâmetros**
    
    * {latitude} - Parâmetro de path que representa a latitude do ponto de referência para a busca.
    * {longitude} - Parâmetro de path que representa a longitude do ponto de referência para a busca.
    * {raio} - Parâmetro de path que representa a distância, a partir do ponto de referência, que serão buscados os CRAS.
    * campos - Parâmetros de query.**Opicional**.Representa a lista de campos a serem retornados. Caso seja omitida, todos os campos serão retornados. Os campos que podem ser retornados são: 
        
        **Observações:** Os campos devem ser passados separados por vígurla e sem espaços em branco. 
    * quantidade - Parâmetro de query define a quantidade máxima de estabelecimentos a serem retornados. Caso não seja informado, utiliza valor padrão igual a 30.
    
    ** Retorno**
        
    
