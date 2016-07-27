#Metamodelo

##API Referece

Esses *endpoints* são responsáveis por fornecer uma infraestrutura para armazenamento de dados de aplicações cívicas. O metamodelo provê serviços como cadastro e armazenamento de usuários genéricos, criação de perfis específicos para determinado aplicativo, login com senha ou com redes sociais **Facebook**, **Twitter**, **Intagram** e **GooglePlus**. Além de dar suporte à dados de usuários o metamodelo também proporciona a criação de grupos de usuário relacionados a um aplicativo, provê também suporte à notificações para aplicativos móveis. Para armazenamento de dados bastante genéricos é dado ao desenvolvedor o objeto de Postagem onde criada uma postagem, pode - se associar vários conteúdos a mesma seja ele objetos da aplicação ou arquivos binários como por exemplo fotos ou vídeos. Os conteúdos que são objetos objetos são salvos como no formato JSON, fazendo com que ele seja dinâmico e genérico podendo armazenar qualquer objeto. Podendo posteriormente alterar, excluir e fazer buscas nos mesmos.

Todos os dados armazenados no metamodelo, que não dizem respeito à dados de usuários ou perfil, são abstraidos como **Postagem** e seus **Conteudos**, sejam eles textos JSON ou arquivos binários. Uma postagem pode ter um ou mais conteúdos, além de poder estar relacionada à uma outra postagem.

## Esquema de Dados
O esquema de dados é relacional e as tabelas estão modeladas da maneira mais genérica possível. Esse modelo de dados descreve como está estruturado o banco de dados onde estão sendo armazenados os usuários, postagens, hashtags, instalações, etc.
### Modelo Físico 
<img src="https://ap.imagensbrasil.org/images/metamodelo-2.jpg" alt="Metamodelo" border="1" width="800">


## URL Base 

`http://mobile-aceite.tcu.gov.br:80/appCivicoRS/`

Clique aqui para testar os endpoints no [Swagger API](http://mobile-aceite.tcu.gov.br/appCivicoRS/swagger/index.html?url=/appCivicoRS/v2/api-docs) 

## Docs

### Aplicativos

* [`GET - /rest/aplicativos`](#buscar-aplicativos)
* [`POST - /rest/aplicativos`](#cadastrar-aplicativo)
* [`GET - /rest/aplicativos/{codAplicativo}`](#informações-de-aplicativo)
* [`PUT - /rest/aplicativos/{codAplicativo}`](#alterar-aplicativo)

### Tipos de Perfil

* [`GET - /rest/aplicativos/{codAplicativo}/tipos-perfil`](#tipos-de-perfil-por-aplicativo)
* [`POST - /rest/aplicativos/{codAplicativo}/tipos-perfil`](#cadastrar-tipo-de-perfil)
* [`GET - /rest/aplicativos/{codAplicativo}/tipos-perfil/{codTipoPerfil}`](#encontrar-tipo-de-perfil)

### Grupos

* [`POST - /rest/grupos`](#criar-grupo)
* [`GET - /rest/grupos/{codGrupo}`](#encontrar-grupo)
* [`DELETE - /rest/grupos/{codGrupo}`](#excluir-grupo)
* [`GET - /rest/grupos/{codGrupo}/membros`](#membros-por-grupo)
* [`POST - /rest/grupos/{codGrupo}/membros`](#adicionar-membro-em-grupo)
* [`GET - /rest/grupos/{codGrupo}/membros/{codMembro}`](#encontrar-membro-em-grupo)

### Hashtags

* [`POST - /rest/hashtags`](#criar-hashtag)
* [`GET - /rest/hashtags/{codHashtag}`](#buscar-hashtag)
* [`PUT - /rest/hashtags/{codHashtag}`](#atualizar-hashtag)
* [`DELETE - /rest/hashtags/{codHashtag}`](#excluir-hashtag)

### Instalações
  
* [`POST - /rest/instalacoes`](#registrar-instalação) 
* [`GET - /rest/instalacoes/{codInstalacao}`](#buscar-instalação)
* [`PUT - /rest/instalacoes/{codInstalacao}`](#alterar-instalação)
  
### Notificações

* [`POST - /rest/notificacoes`](#registrar-notificação)
* [`GET - /rest/notificacoes/{codNotificacao}`](#buscar-notificação)
* [`PUT - /rest/notificacoes/{codNotificacao}`](#alterar-notificação)

### Pessoas

* [`GET - /rest/pessoas`](#buscar-pessoa)
* [`POST - /rest/pessoas`](#cadastrar-pessoa)
* [`GET - /rest/pessoas/autenticar`](#autenticar)
* [`POST - /rest/pessoas/redefinirSenha`](#redefinir-senha)
* [`GET - /rest/pessoas/{codPessoa}`](#encontrar-pessoa)
* [`POST - /rest/pessoas/{codPessoa}`](#atualizar-pessoa)
* [`DELETE - /rest/pessoas/{codPessoa}`](#excluir-cadastro)
* [`POST - /rest/pessoas/{codPessoa}/definirNovaSenha`](#alterar-senha)
* [`GET - /rest/pessoas/{codPessoa}/fotoPerfil`](#foto-de-perfil)
* [`POST - /rest/pessoas/{codPessoa}/fotoPerfil`](#cadastrar-foto-de-perfil)

### Perfis

* [`GET - /rest/pessoas/{codPessoa}/perfil`](#buscar-perfil)
* [`POST - /rest/pessoas/{codPessoa}/perfil`](#cadastrar-perfil)
* [`DELETE - /rest/pessoas/{codPessoa}/perfil`](#excluir-perfil)
* [`PUT - /rest/pessoas/{codPessoa}/perfil`](#alterar-perfil)

### Pessoas e Postagens

* [`GET - /rest/pessoas/{codPessoa}/postagens`](#buscar-postagens-de-pessoa)

### Postagens

* [`GET - /rest/postagens`](#buscar-postagens)
* [`POST - /rest/postagens`](#cadastrar-postagem)
* [`GET - /rest/postagens/{codPostagem}`](#encontrar-postagem)
* [`DELETE - /rest/postagens/{codPostagem}`](#excluir-postagem)

### Avaliações de Objeto

* [`GET - /rest/postagens/tipopostagem/{codTipoPostagem}/tipoobjeto/{codTipoObjetoDestino}/objeto/{codObjetoDestino}`](#média-de-avaliações)

### Conteudos de Postagens

* [`POST - /rest/postagens/{codPostagem}/conteudos`](#criar-conteúdo-de-postagem)
* [`GET - /rest/postagens/{codPostagem}/conteudos/{codConteudo}`](#encontrar-conteudo-de-postagem)
* [`PUT - /rest/postagens/{codPostagem}/conteudos/{codConteudo}`](#alterar-conteúdo-de-postagem)
* [`DELETE - /rest/postagens/{codPostagem}/conteudos/{codConteudo}`](#excluir-conteúdo-de-postagem)
* [`GET - /rest/postagens/{codPostagem}/conteudos/{codConteudo}/conteudoBinario`](#encontrar-conteúdo-binário-de-postagem)
* [`POST - /rest/postagens/{codPostagem}/conteudos/{codConteudo}/conteudoBinario`](#criar-conteúdo-binário-de-postagem)


### Tipos de objeto
  
  Tipos de objeto são usuados para relacionar o metamodelo com as bases que contém os dados abertos, como por exemplo, as bases de remédios, estabelecimentos de saúde, escolas, entre outras. Essa relação é feita através da postagem, pelo campo tipoObjetoDestino, onde se pode criar postagens relacionadas à uma entidade de dados aberto, como por exemplo uma escola. Além desse código do tipo de objeto destino essa relação ainda necessita do código do objeto destino, ou seja, o código único que identifica uma escola, estabelecimento de saúde ou outra entidade qualquer. Essa relação pode ser usada de várias maneiras para contruir aplicações, um bom exemplo disso é um aplicativo que faça avaliações de escolas, essa avaliações podem ser salvas como postagem, onde o código do tipoObjetoDestino é **1**(código do tipo objeto que representa uma escola) e o código objeto destino seria o código identificador da escola.  

### Tipos de postagem

* [`GET - /rest/tipos-postagem`](#buscar-tipos-de-postagem)
* [`POST - /rest/tipos-postagem`](#registrar-tipo-de-postagem)
* [`GET - /rest/tipos-postagem/{codTipoPostagem}`](#encontrar-tipo-de-postagem)
* [`PUT - /rest/tipos-postagem/{codTipoPostagem}`](#alterar-tipo-de-postagem)



#Aplicativos

### Buscar Aplicativos
  
  Esse **endpoint** retorna informações todos os aplicativos registrados na plataforma.
  
* `GET - /rest/aplicativos`

  **Parâmetros**
      
  Não há parâmetros.

  **Retorno**
    
    * 200 - OK
      
      **Exemplo**
      
      ````
        {
          "links": [
            {
              "rel": "self",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/22"
            },
            {
              "rel": "responsavel",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/1"
            }
          ],
          "cod": 22,
          "nome": "VacinApp",
          "descricao": "Aplicativo para gerência de cartão de vacina digital"
        }
      ```
      
### Cadastrar Aplicativo
    
  Esse **endpoint** cadastra um aplicativo na plataforma.

* `POST - /rest/aplicativos`

  **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
      
    * **body** - Campos com informações sobre o aplicativo.
      
        * codResponsavel - Código do desenvolvedor responsável pelo aplicativo.
        * descricao - Breve descrição do aplicativo. Explicação sobre o que o aplicativo faz, qual àrea de abordagem, e sobre que tipo de informação esse aplicativo armazena na plataforma.
        * nome - Nome do aplicativo.
        * token - Identificador único e secreto de um aplicativo. **Opcional**
        
      **Exemplo**
        
        ````
            {
              "codResponsavel": 1,
              "descricao": "Aplicativo para visualizar informações sobre estabelecimentos de saúde",
              "nome": "Mapa da Saúde",
              "token": ""
            }
        ```
        
  **Retorno**
  
    * 201 - Aplicação criada com sucesso.
    
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados do aplicativo no campo **location**. 
        
        ````
            "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/25"
        ```
        
    * 401 - Não autorizado.
    
        O apptoken enviado não é um token válido ou está expirado.
        
    * 400 - Parâmentros incorretos
    
        Falta de parâmetros obrigatórios ou parâmetros incorretos.
    * 404 - Responsável não encontrado
        Não exite uma pessoa cadastrada com o código informado no campo **codResponsavel**.
        
### Informações de Aplicativo
  
  Este *endpoint* retorna informações de um aplicativo especifico buscado por código do mesmo.
  
* `GET - /rest/aplicativos/{codAplicativo}`

  **Parâmetros**
  
    * {codAplicativo} - Parâmetro de path que representa o código do aplicativo a ser buscado.
  
  **Retorno**
    
    * 200 - OK
      
      **Exemplo**
      
      ````
        {
          "links": [
            {
              "rel": "self",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/22"
            },
            {
              "rel": "responsavel",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/1"
            }
          ],
          "cod": 22,
          "nome": "VacinApp",
          "descricao": "Aplicativo para gerência de cartão de vacina digital"
        }
      ```
      
    * 404 - Aplicativo não encontrado
      
      Não existe um aplicativo cadastrado com o código mandado como parâmtro na busca.
    
### Alterar Aplicativo

  Esse **endpoint** altera informações de um aplicativo cadastrado na plataforma.
  

* `PUT - /rest/aplicativos/{codAplicativo}`
  
  **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codAplicativo} - Parâmetro de path que representa o código do aplicativo a ser alterado.

    * **body** - Campos com as novas informações sobre o aplicativo.
      
        * codResponsavel - Código do desenvolvedor responsável pelo aplicativo.
        * descricao - Breve descrição do aplicativo. Explicação sobre o que o aplicativo faz, qual àrea de abordagem, e sobre que tipo de informação esse aplicativo armazena na plataforma.
        * nome - Nome do aplicativo.
        * token - . **Opcional**
        
      **Exemplo**
        
        ```
            {
              "codResponsavel": 1,
              "descricao": "Aplicativo para visualizar informações sobre estabelecimentos de saúde",
              "nome": "Mapa da Saúde",
              "token": ""
            }
        ```
  **Retorno**
  
    * 200 - Alterado com sucesso.
    
        Os dados foram alterados com sucesso.
        
    * 401 - Não autorizado.
    
        O apptoken enviado não é um token válido ou está expirado.
        
    * 400 - Parâmentros incorretos
    
        Falta de parâmetros obrigatórios ou parâmetros incorretos.
        
    * 404 - Aplicativo ou responsável não encontrado 
      
      Não existe um aplicativo cadastrado com o código mandado como parâmtro na busca ou um responsável com o código informado no campo **codResponsavel**.
  
# Tipos de Perfil
  
  Para cada aplicativo é possível criar perfis para um usuário já cadastrado na base na plataforma. Através do tipo de perfil é possível ter diferentes tipos de usuário em um determinado aplicativo.
    
### Tipos de Perfil por aplicativo

  Este *endpoint* retorna os tipos de perfil criados para um determinado aplicativo.

* `GET - /rest/aplicativos/{codAplicativo}/tipos-perfil`

  **Parâmetros**
    
    * {codAplicativo} - Parâmetro de path que indica o código do aplicativo em que os perfis serão buscados.
    * pagina - Parâmetro de query opcional para uma busca paginada. **Opcional**. Número da página com valor padrão 0.
    * quantidadeDeItens - Parâmetro de query opcional que define o máximo de escolas retornadas na busca. **Opcional**.Valor padrão é 20.
  
  **Retorno**
  
    * 200 - Ok.
      
      **Exemplo**
        
        ```
          [
            {
              "links": [
                {
                  "rel": "self",
                  "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/100/tipos-perfil/2"
                },
                {
                "rel": "aplicativo",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/100"
                }
              ],
              "codTipoPerfil": 2,
              "descricao": "Administrador",
              "dataHoraCriacao": "2015-11-30T00:00:00BRST"
            }
          ]
        ```
    
    * 404 - Aplicativo com o código mandado como parâmetro não encontrado.
    
### Cadastrar Tipo de Perfil

  Cadastra um novo tipo de perfil para um aplicativo.

* `POST - /rest/aplicativos/{codAplicativo}/tipos-perfil`
  
   **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    * {codAplicativo} - Código do aplicativo para qual será criado o novo tipo de perfil.
    * **body** - Campos com informações sobre o tipo de perfil.
      
        * descricao - Descrição do tipo de perfil.
    
      **Exemplo**
        
        ```
            {
              "descricao": "Descrição do tipo de perfil."
            }
        ```
        
  **Retorno**
  
    * 201 - Tipo de perfil criado com sucesso.
    
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados do tipo de perfil no campo **location**. 
        
        ````
        "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/25/tipos-perfil/41"
        ```
        
    * 401 - Não autorizado.
    
        O apptoken enviado não é um token válido ou está expirado.
        
    * 400 - Parâmentros incorretos
    
        Falta de parâmetros obrigatórios ou parâmetros incorretos.
    * 404 - Aplicativo não encontrado
        Não exite uma aplicativo cadastrado com o código informado.

### Encontrar Tipo de Perfil
  
  Este *endpoint* retorna informações de um tipo de perfil especifico buscado por código do mesmo.

* `GET - /rest/aplicativos/{codAplicativo}/tipos-perfil/{codTipoPerfil}`
  
  **Parâmetros**
    
    * {codAplicativo} - Parâmetro de path que indica código do aplicativo.
    * {codTipoPerfil} - Parâmtro de path que indica código do tipo de perfil a ser buscado.
  **Retorno**
  
    * 200 - 0k
    
        ```
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/25/tipos-perfil/41"
              },
              {
                "rel": "aplicativo",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/25"
              }
            ],
            "codTipoPerfil": 41,
            "descricao": "administrador",
            "dataHoraCriacao": "2016-05-29T15:11:00BRT"
          }
        ```
        
    * 404 - Não encontrado.
    
        Não foi encontrado um tipo de perfil com esse código nesse aplicativo.
  
  
# Grupos

  Assim como diferentes perfis, para cada aplicativo é possível criar é possível grupos de usuários em um aplicativo. Onde se pode adicionar membros cadastrados na plataforma pelo seu código de usuário.

### Criar grupo

  Este *endpoint* é responsável por criar um novo grupo de usuários para um aplicativo.

* `POST - /rest/grupos` 

  **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
      
    * **body** - Campos com informações sobre o grupo.
    
      * codAplicativo - Código do aplicativo à qual o grupo pertence.
      * codGrupoPai - **Opcional**. Para criação de subgrupos em hieraquia e indica de qual grupo, esse grupo é um subgrupo.
      * codObjeto -  **Opcional**. Código do objeto à qual esse grupo está associado.
      * codTipoObjeto -  **Opcional**. Código do tipo de objeto à qual esse grupo está associado.
      * descricao - Descrição do grupo.
      
      **Exemplo**
      
      ````
      {
        "codAplicativo": 0,
        "codGrupoPai": 0,
        "codObjeto": 0,
        "codTipoObjeto": 0,
        "descricao": "string"
      }
      ```
  
  **Retorno**

  * 201 - Grupo criado com sucesso.
    
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados do grupo no campo **location**. 
        
        ```
          "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/grupos/2"
        ```
        
  * 401 - Não autorizado.
    
    O apptoken enviado não é um token válido ou está expirado.
        
  * 400 - Parâmentros incorretos
    
    Falta de parâmetros obrigatórios ou parâmetros incorretos.
  * 404 - Aplicativo não encontrado
  
    Não exite um aplicativo cadastrado com o código informado no campo **codAplicativo**.    


### Encontrar Grupo

  Este *endpoint* retorna informações de um grupo especifico buscado por código do mesmo.

* `GET - /rest/grupos/{codGrupo}`

   **Parâmetros**
    
    * {codGrupo} - Parâmetro de path que indica o código do grupo a ser buscado.
  
  **Retorno**
    
    * 200 - Ok
      
      **Exemplo**
      
      ```
        {
          "links": [
            {
              "rel": "self",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/grupos/1"
            },
            {
              "rel": "aplicativo",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/100"
            },
            {
              "rel": "tipoObjeto",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/tipos-objeto/100"
            }
          ],
          "descricao": "teste",
          "codObjeto": 0
        }
      ```
      
    * 404 - Grupo não encontrado.

### Excluir Grupo

  Esse *endpoint* exclui determinado grupo por código.
  
* `DELETE - /rest/grupos/{codGrupo}`
  
   **Parâmetros** 
    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codGrupo} - Parâmetro de path. Indica o código do grupo a ser excluído.
  
  **Retorno**
    
    * 200 - Ok    
      
      Excluído com sucesso.
      
    * 404 - Não encontrado.
      
      Grupo com o código informada não se encontra cadastrada.

    * 401 - Não autorizado
      
      O apptoken enviado não é um token válido ou está expirado.

    * 400 - Parâmetros inconsistentes.


### Membros por Grupo

  Este *endpoint* retorna o membros de determinado grupo.
  
* `GET - /rest/grupos/{codGrupo}/membros`

   **Parâmetros**
    
    * {codGrupo} - Parâmetro de path que indica o código do grupo a ser buscado.
  
  **Retorno**
    
    * 200 - Ok
    
      **Exemplo**
      
      ```
        [
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/grupos/1/membros/1"
              },
              {
                "rel": "pessoa",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/27"
              }
            ],
            "dataHoraAtivo": "2016-02-18T22:50:35BRST"
          }
        ]
      ```
      
    * 404 - Grupo não encontrado.
  
### Adicionar membro em Grupo

  Adiciona uma pessoa como membro de um grupo.
  
* `POST - /rest/grupos/{codGrupo}/membros` 
  
  **Parâmetros**
  
    **www-form-urlencoded**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    * {codGrupo} - Parâmetro de path que indica o código do grupo a ser buscado.
    * **body** - Campos com informações do membro
      
      * codUsuario - Código da pessoa que será adicionada como membro.
  
  **Retorno**

  * 201 - Membro criado com sucesso.
    
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados do membro no grupo no campo **location**. 
        
        ```
          "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/grupos/2/membros/2"
        ```
        
  * 401 - Não autorizado.
    
    O apptoken enviado não é um token válido ou está expirado.
        
  * 400 - Parâmentros incorretos
    
    Falta de parâmetros obrigatórios ou parâmetros incorretos.
  * 404 - Não encontrado
  
    Não exite um grupo cadastrado com o código informado ou não existe uma pessoa cadastrada com o código informado no campo **codUsuario**.    

### Encontrar membro em Grupo

  Esse *endpoint* é responsável por encontrar um membro em determinado grupo.
  
* `GET - /rest/grupos/{codGrupo}/membros/{codMembro}`

  **Parâmetros**
    
    * {codGrupo} - Parâmetro de path que representa o código do grupo. 
    * {codMembro} - Parâmetro de path que representa o código do membro.
  
  **Retorno**
    
    * 200 - Ok
      
      **Exemplo**
      
        ```
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/grupos/2/membros/2"
              },
              {
                "rel": "pessoa",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/27"
              }
            ],
            "dataHoraAtivo": "2016-05-29T16:38:32BRT"
          }
        ```
    * 404 - Não encontrado
      Grupo com código especificado não encontrado ou pessoa com o código especificado não encontrada ou a pessoa não é membro desse grupo.

# Hashtags
      
  Para cada postagem genérica armazenada na plataforma é possível associar **hashtags** à elas. Hashtags são palavras chave com algum significado. As hashtags na plataforma seguem o mesmo princípio de hashtags usadas em redes sociais como [**Twitter**](https://twitter.com/), [**Facebook**](https://www.facebook.com/).

### Criar Hashtag

  Cria uma nova hashtag.

* `POST - /rest/hashtags`

 **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
      
    * **body** - Campos com informações sobre a hashtag.
    
      * codAplicativo - Código do aplicativo à qual a hashtag pertence.
      * descricao - Descrição da hash tag
      * nome - Representa a hashtag em si. Deve ser sempre iniciado com # e sem espaços em branco.
  
      **Exemplo**
      
      ````
        {
          "codAplicativo": 100,
          "descricao": "string",
          "nome": "#test"
        }
      ```
      
  **Retorno**
  
    * 201 - Hashtag criada com sucesso.
      
        Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados da hashtag no campo **location**. 
          
          ```
              "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/hashtags/24"
          ```
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou hashtag já está cadastrada.
      
    * 404 - Não encontrado
      
      Aplicativo com o código passado no campo **codAplicativo** não foi encontrado.

### Buscar Hashtag

  Busca o conteúdo de uma hashtag pelo código da mesma.

* `GET - /rest/hashtags/{codHashtag}`

  **Parâmetros**
  
    * {codHashtag} - Parâmetro de path que representa o código da hashtag a ser buscada.
  
  **Retorno**
    
    * 200 - Ok
    
      **Exemplo**
        
        ````
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/hashtags/24"
              },
              {
                "rel": "aplicativo",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/100"
              }
            ],
            "nome": "#test",
            "descricao": "string"
          }
          
        ```
    * 404 - Não encontrado
        Hashtag não encontrada.
      
### Atualizar Hashtag

  Altera dados de uma hashtag criada.
  
* `PUT - /rest/hashtags/{codHashtag}`

  **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codHashtag} - Parâmetro de path que representa o código da hashtag a ser alterada.

    * **body** - Campos com informações sobre a hashtag.
    
      * codAplicativo - Código do aplicativo à qual a hashtag pertence.
      * descricao - Descrição da hash tag
      * nome - Representa a hashtag em si. Deve ser sempre iniciado com # e sem espaços em branco.
  
      **Exemplo**
      
      ````
        {
          "codAplicativo": 100,
          "descricao": "string",
          "nome": "#test"
        }
      ```
  
  **Retorno**
  
    * 200 - Hashtag alterada com sucesso.
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou hashtag já está cadastrada.
      
    * 404 - Não encontrado
      
      Hashtag não encontrada ou aplicativo com o código passado no campo **codAplicativo** não foi encontrado.

### Excluir Hashtag
  
  Permite a exclusão de uma hashtag desde que não tenha postagens relacionadas.

* `DELETE - /rest/hashtags/{codHashtag}`
  
    **Parâmetros** 
    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codHashtag} - Parâmetro de path. Indica o código da hashtag a ser excluída.
  
  **Retorno**
    
    * 200 - Ok    
      
      Excluído com sucesso.
      
    * 404 - Não encontrado.
      
      Hashtag com o código informada não se encontra cadastrada.

    * 401 - Não autorizado
        
      O apptoken enviado não é um token válido ou está expirado.
  
    * 400 - Parâmetros inconsistentes.



# Instalações

  Instalações associam um dispositivo à um usuário para seja possível manter um histórico de pessoas que baixaram e estão usando os aplicativos.

### Registrar Instalação

  Registra uma instalação em um aplicativo.
  
* [`POST - /rest/instalacoes`] 

  **Parâmetros**
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
  
    * **body** - Campos com informações sobre a instalação.
    
      * codApp - Código do aplicativo no qual a instalação está sendo feita.
      * codUsuario - Código do usuário associado à instalação. Quando uma notificação for criada ela será enviada para todas as instalações associadas ao usuário.
      * dataHora - Data e hora da instalação.
      * deviceOS -  Sistema operacional do dispositivo.
      * deviceToken - Identificador único de um dispositivo.

      **Exemplo**
      
      ````
        {
          "codApp": 1,
          "codUsuario": 27,
          "dataHora": "2016-05-29T15:27:19.256Z",
          "deviceOS": "iOS",
          "deviceToken": "DSJK-DJKA-D312-312N-3213-E232-DSAL"
        }
      ```
  
  **Retorno**
  
    * 201 - Instalação criada com sucesso.
      
        Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados da instalação no campo **location**. 
          
          ```
            "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/instalacoes/2",
          ```
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou device token já está registrado.
      
    * 404 - Não encontrado
      
      Aplicativo com o código passado no campo **codAplicativo** não foi encontrado ou usuário com o código passado no campo **codUsuario** não foi encontrado. 

### Encontrar Instalação

  Encontrar dados de uma instalação através do código.
  
* `GET - /rest/instalacoes/{codInstalacao}`

  **Parâmetros**
  
    * {codInstalacao} - Parâmetro de path que representa o código da instalação a ser buscada.
  
  **Retorno**
    
    * 200 - Ok
    
      **Exemplo**
        
        ````
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/instalacoes/3"
              },
              {
                "rel": "aplicativo",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/100"
              },
              {
                "rel": "pessoa",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/27"
              }
            ],
            "deviceOS": "iOS",
            "dataHora": "2016-05-29T12:27:19BRT",
            "deviceToken": "78921dd331232131"
          }
        ```
    * 404 - Não encontrado
        Instalação não encontrada.
      
### Alterar Instalação

  Alterar dados de uma instalação.
  
* `PUT - /rest/instalacoes/{codInstalacao}`

  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    * {codInstalacao} - Parâmetro de path que representa o código da instalação a ser alterada.
    
    * **body** - Campos com informações sobre a instalação.
    
      * codApp - Código do aplicativo no qual a instalação está sendo feita.
      * codUsuario - Código do usuário associado à instalação. Quando uma notificação for criada ela será enviada para todas as instalações associadas ao usuário.
      * dataHora - Data e hora da instalação.
      * deviceOS -  Sistema operacional do dispositivo.
      * deviceToken - Identificador único de um dispositivo.

      **Exemplo**
      
      ````
        {
          "codApp": 1,
          "codUsuario": 27,
          "dataHora": "2016-05-29T15:27:19.256Z",
          "deviceOS": "iOS",
          "deviceToken": "DSJK-DJKA-D312-312N-3213-E232-DSAL"
        }
      ```
  
  **Retorno**
  
    * 200 - Instalação alterada com sucesso.
      
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou device token já está registrado.
      
    * 404 - Não encontrado
      
      Aplicativo com o código passado no campo **codAplicativo** não foi encontrado ou usuário com o código passado no campo **codUsuario** não foi encontrado. 

# Notificações
  
  Através das notificações é possível armazenar ações feitas pelos usuários dentro dos aplicativos para que se possa mostrar posteriormente. É importante lembrar que a estrutura de notificação **não** fornece o serviço de #[Push Notifications](http://fabricadeaplicativos.com.br/fabrica/o-que-e-e-como-funciona-a-notificacao-push/), os endpoits de notificação são apenas para armazenamento. 

### Registrar Notificação
  
  Registrar uma notificação.
  
* [`POST - /rest/notificacoes`]
  
  **Parâmetros**
  
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * **body** - Campos com informações sobre a notificação.
    
      * JSON - Corpo da notificação
        * autor - **Opcional**
          * codPessoa - Código do usuário que criou a notificação.
        * post -  **Opcional**
          * codPost - Código da postagem associada à notificação.
        * tipo - Tipo de notificação.
      * dataHoraLeitura - Data e hora que a notificação foi aberta pelo destinatário.
      * descricao - Descrição da notificação.
      * destinatario  
        * codPessoa - Código do usuário que será direcionada a notificação. 
    
      **Exemplo**
      
      ```
        {
          "JSON": {
            "autor": {
              "codPessoa": 21
            },
            "post": {
              "codPost": 10
            },
            "tipo": "curtida"
          },
          "dataHoraLeitura": "2016-05-29T15:27:19.259Z",
          "descricao": "Descrição",
          "destinatario": {
            "codPessoa": 27
          }
        }
      ```
  
  **Retorno**
  
    * 201 - Notificação criada com sucesso.
      
        Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados da notificação no campo **location**. 
          
          ```
            "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/notificacoes/5"
          ```
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou device token já está registrado.
      
    * 404 - Não encontrado
      
      Usuário com o código passado no campo **autor.codPessoa** não foi encontrado ou usuário com o código passado no campo **destinatario.codPessoa** não foi encontrado.   


### Buscar Notificação
  
  Encontrar uma notificação pelo código.
  
* `GET - /rest/notificacoes/{codNotificacao}`

  **Parâmetros**
  
  * {codNotificacao} - Parâmetro de path que representa o código da notificação a ser buscada.
  
  **Retorno**
    
    * 200 - Ok
    
      **Exemplo**
        
        ```
          {
            "descricao": "string",
            "destinatario": {
              "codPessoa": 27
            },
            "JSON": {
              "tipo": "string"
            }
          }
        ```
    * 404 - Não encontrado
        Instalação não encontrada.

### Alterar Notificação
  
  Altera dados da notificação.
  
* [`PUT - /rest/notificacoes/{codNotificacao}`](#alterar-notificação)  

  **Parâmetros**
  
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * **body** - Campos com informações sobre a notificação.
    
      * dataHoraLeitura - Data e hora que a notificação foi aberta pelo destinatário.
      
      **Exemplo**
      
      ```
        {
          "dataHoraLeitura": "2016-05-29T15:27:19.259Z"
        }
      ```
      
  **Retorno**
  
    * 200 - Notificação alterada com sucesso.
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou device token já está registrado.
      
# Pessoas

  A estrutura de pessoa provê juntamente com a estrutura de perfil, o gerenciamento de usuário e suas informações em aplicativos através da plataforma. A estrutura de pessoa permite o cadastro de dados básicos de uma pessoa.

### Buscar Pessoa
  
  Busca pessoas cadastrada por parâmetros como nome completo ou parte do nome, e-mail, facebookToken, googleToken, twitterToken entre outros.
  
* `GET - /rest/pessoas`
  
  **Parâmetros**
  
    * codAplicativo - Parâmetro de query. **Opcional**. Código do aplicativo onde as pessoas possuem um perfil.
    * nome - Parâmetro de query. **Opcional**. Nome completo ou parte do nome.
    * email - Parâmetro de header. **Opcional**. E-mail da pessoa.
    * facebookToken - Parâmetro de header. **Opcional**. Facebook id que irá buscar a pessoa cadastrada com o mesmo.
    * googleToken - Parâmetro de header. **Opcional**. GooglePlus id que irá buscar a pessoa cadastrada com o mesmo.
    * twitterToken - Parâmetro de header. **Opcional**. Twitter id que irá buscar a pessoa cadastrada com o mesmo.
    * instagramToken - Parâmetro de header. **Opcional**. Instagram id que irá buscar a pessoa cadastrada com o mesmo.
    * pagina - Parâmetro de query. **Opcional**. Valor padrão 0. Para uma busca paginada.
    * quantidadeDeItens - Parâmetro de query. **Opcional**. Define o máximo de pessoas retornadas na busca. Valor padrão é 20.
    
  **Retorno** 
    
    * 200 - Ok 
    
      Pessoas com dados que satisfazem os parâmetros de busca encontradas.
      
      **Exemplo** 
      
        ```
          [
            {
              "links": [
                {
                  "rel": "self",
                  "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/31"
                }
              ],
              "nomeUsuario": "Luciano",
              "cod": 31,
              "email": "passos.luciano@outlook.com",
              "emailVerificado": false
            }
          ]
        ```
      
    * 204 - Nenhum dado encontrado
      
      Nenhuma pessoa com dados que satisfazem os parâmetros de busca foi encontrada.
      
    * 400 - Parâmentros incorretos
      
      Parâmetros inconsistentes em tipo ou sintaxe.

### Cadastrar Pessoa

  Permite o cadastro de uma pessoa na plataforma.

* `POST - /rest/pessoas`

  **Parâmetros**
  
  **aplication/json**
    
    * **body** - Campos com informações sobre a pessoa.  
      
      * CEP - **Opcional**. Representa o CEP do endereço onde a pessoa mora.
      * biografia - **Opcional**. Pequeno texto sobre a pessoa. Máximo 250 caracteres.
      * dataNascimento - **Opcional**. Data de nascimento da pessoa no formato yyyy-MM-dd'T'hh:mm:ss.SSSz.
      * email - E-mail da pessoa.
      * latitude - **Opcional**. Referente a latitude da localização da pessoa.
      * longitude - **Opcional**. Referente a longitude localização da pessoa.
      * nomeCompleto - Nome completo da pessoa.
      * senha - **Opcional**. Senha de cadastro do usuário. Caso seja um cadastro de uma rede social não é necessário, porém deve ser passado alguém token social para cadastro.
      * sexo - **Opcional**. Deve ser passado "M" para masculino e "F" para feminino.
      * tokenFacebook - **Opcional**. Id obtido por autenticação do usuário pela API do facebook para cadastro com facebook.
      * tokenGoogle - **Opcional**. Id obtido por autenticação do usuário pela API do GooglePlus para cadastro com GooglePlus.
      * tokenInstagram - **Opcional** Id obtido por autenticação do usuário pela API do Instagram do usuário para cadastro com o Instagram.
      * tokenTwitter - **Opcional**. Id obtido por autenticação do usuário pela API do Twitter do usuário para cadastro com o Twitter.
      
      **Exemplo**
        
        ```
          {
            "CEP": "7454555",
            "biografia": "Minha história",
            "dataNascimento": "2016-06-07T01:33:22.740Z",
            "email": "email@mail.com",
            "latitude": 12,
            "longitude": 10,
            "nomeCompleto": "José da Silva",
            "nomeUsuario": "José",
            "senha": "string",
            "sexo": "M",
            "tokenFacebook": "32131423243",
            "tokenGoogle": "43243243",
            "tokenInstagram": "423432432423423",
            "tokenTwitter": "6456546457423904923"
          }
        ```
  **Retorno** 
    
    * 201 - Cadastrado com sucesso.
    
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados da pessoa no campo **location**.
      
        ```
          "location": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/438"
        ```
    * 400 - Parâmentros incorretos
    
      Algum parâmetros está inconsistente ou o json está mal formatado ou e-mail já se encontra cadastrado. A mensagem de erro vai no corpo da resposta.
    
### Autenticar

  Autentica o usuário gerando para o mesmo um token de acesso para realizar operações que exigem autenticação. O token gerado é válido por 7 dias.

* `GET - /rest/pessoas/autenticar`
  
  **Parâmetros**
    
    * appIdentifier - Parâmetro de header. **Optional**. Código do app, caso a autenticação exija que a pessoa possua um perfil no aplicativo.
    * email - Parâmetro de header. e-mail da pessoa.
    * senha - Parâmetro de header. **Optional**. Para login com conta padrão da plataforma. Caso seja um login com alguma rede social, é um parâmetro opcional.
    * facebookToken - Parâmetro de header. **Optional**. Para login com a API do facebook.
    * googleToken - Parâmetro de header. **Optional**. Para login com a API do GooglePlus.
    * twitterToken - Parâmetro de header. **Optional**. Para login com a API do Twitter.
  
  **Retorno**
  
    200 - Autenticado com sucesso
      Retorna os dados da pessoa no **body** da resposta. E o token de autenticação no campo **header** da resposta .
      
      **Header** 
        ```
            "apptoken": "v1_BCA83DBAB23B22B1F6510C9D3F947A9B4652CD87448ECE73FD7B99CCC72C2102BBF804D4D42EF841CED193506F905CD332BF57386AF3F52253133F88*********************************************************"

        ```
        
      **Body***
      ```
        {
          "links": [
            {
              "rel": "self",
              "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/27"
            }
          ],
          "nomeUsuario": "LucianoPP",
          "nomeCompleto": "string",
          "cod": 27,
          "email": "ucb.luciano@gmail.com",
          "emailVerificado": false
        }
        
      ```
      
      
    401 - Credenciais inválidas
      
      Usuário ou senha incorretos.
      
    400 - Parâmetros incorretos
      
      Falta de parâmetros ou parâmetros inconsistentes.
      
### Redefinir Senha

  Usado para funcionalidade de esqueci minha senha. O servidor gera uma nova senha aleatória para o usuário e envia para o email do mesmo.
  
* `POST - /rest/pessoas/redefinirSenha`

  **Parâmetros**
    
    * email - E-mail do cadastro que terá a senha resetada.
    
  **Retorno**
  
    * 200 - Senha redefinida com sucesso.
  
    * 404 - E-mail informado não se encontra cadastrado.

### Encontrar Pessoa

  Encontra informações de uma pessoa através do código da mesma.

* `GET - /rest/pessoas/{codPessoa}`

  **Parâmetros**
  
    * {codPessoa} - Parâmetro de path. Indica o código a ser buscado.
  
  **Retorno**
  
    * 200 - Ok
    
      **Exemplo**
        
        ```
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/27"
              }
            ],
            "nomeUsuario": "LucianoPP",
            "nomeCompleto": "string",
            "cod": 27,
            "email": "ucb.luciano@gmail.com",
            "emailVerificado": false
          }
        ```
    * 404 - Não encontrado
        Pessoa não encontrada.

### Atualizar pessoa

  Alterar dados cadastrais de uma pessoa.
  
* `POST - /rest/pessoas/{codPessoa}`

  **Parâmetros**
  
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa a ser alterada.

    * **body** - Campos com informações sobre a pessoa.
    
      * CEP - **Opcional**. Representa o CEP do endereço onde a pessoa mora.
      * biografia - **Opcional**. Pequeno texto sobre a pessoa. Máximo 250 caracteres.
      * dataNascimento - **Opcional**. Data de nascimento da pessoa no formato yyyy-MM-dd'T'hh:mm:ss.SSSz.
      * email - **Opcional**. E-mail da pessoa.
      * latitude - **Opcional**. Referente a latitude da localização da pessoa.
      * longitude - **Opcional**. Referente a longitude localização da pessoa.
      * nomeCompleto - **Opcional**. Nome completo da pessoa.
      * sexo - **Opcional**. Deve ser passado "M" para masculino e "F" para feminino.
      * tokenFacebook - **Opcional**. Id obtido por autenticação do usuário pela API do facebook para cadastro com facebook.
      * tokenGoogle - **Opcional**. Id obtido por autenticação do usuário pela API do GooglePlus para cadastro com GooglePlus.
      * tokenInstagram - **Opcional** Id obtido por autenticação do usuário pela API do Instagram do usuário para cadastro com o Instagram.
      * tokenTwitter - **Opcional**. Id obtido por autenticação do usuário pela API do Twitter do usuário para cadastro com o Twitter.
      
      **Exemplo**
        
        ```
          {
            "CEP": "7454555",
            "biografia": "Minha história",
            "dataNascimento": "2016-06-07T01:33:22.740Z",
            "email": "email@mail.com",
            "latitude": 12,
            "longitude": 10,
            "nomeCompleto": "José da Silva",
            "nomeUsuario": "José",
            "senha": "string",
            "sexo": "M",
            "tokenFacebook": "32131423243",
            "tokenGoogle": "43243243",
            "tokenInstagram": "423432432423423",
            "tokenTwitter": "6456546457423904923"
          }
        ```
  **Retorno**
  
    * 200 - Ok    
      
      Alterado com sucesso.
      
    * 404 - Não encontrado.
      
      Pessoa com o código informada não se encontra cadastrada.
    
### Excluir cadastro
  
  Exclui permanentemente dados cadastrais de uma pessoa.
  **Obs:** Essa é uma ação que não pode ser desfeita. Certifique-se de sempre pedir confirmações por parte do usuário.
  
* `DELETE - /rest/pessoas/{codPessoa}`
  
  **Parâmetros** 
    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa a ser excluída.
  
  **Retorno**
    
    * 200 - Ok    
      
      Excluído com sucesso.
      
    * 404 - Não encontrado.
      
      Pessoa com o código informada não se encontra cadastrada.

    * 401 - Não autorizado
        
        Senha atual incorreta.
        
    * 400 - Parâmetros inconsistentes.
    
### Alterar Senha
  
  Altera a senha atual do usuário.

* `POST - /rest/pessoas/{codPessoa}/definirNovaSenha`

 **Parâmetros** 
    
    **www-form-urlencoded**
    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
  
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa que irá alterar a senha.
  
    * email - e-mail do usuário que deseja alterar senha.
    * senhaAtual - Senha atual para autenticação antes da alteração.
    * novaSenha - Nova senha do usuário.
    
  **Retorno**
    
    * 200 - Ok    
      
      Senha alterada com sucesso.
      
    * 404 - Não encontrado.
      
      Pessoa com o código informada não se encontra cadastrada.
      
    * 401 - Não autorizado
        
        Senha atual incorreta.
        
    * 400 - Parâmetros inconsistentes.

### Foto de Perfil

  Buscar foto de perfil.
  
* `GET - /rest/pessoas/{codPessoa}/fotoPerfil`
  
  **Parâmetros** 
    
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa que irá ser buscada a foto.
  
  **Retorno**
    
    * 200 - Ok 
      
      Retorna no **body** da resposta o conteudo da foto. Retorno no tipo   **"content-type": "image/jpeg"**

    * 404 - Não encontrada
    
      Usuário não possui foto. Retorno do tipo: **"content-type": "application/json;charset=UTF-8"**
    
### Cadastrar foto de perfil

  Cadastra a foto de perfil do usuário. Caso já exista uma foto, a mesma será sobrescrita.
  
* `POST - /rest/pessoas/{codPessoa}/fotoPerfil`

  **Parâmetros** 
    
    **multipart/form-data**
    
     * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
  
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa que irá registra a foto.
    
    * file - Parâmetro do formuário que representa o conteúdo do arquivo de foto.
    
  **Retorno**
    
    * 200 - Ok    
      
      Foto salva com sucesso.
      
    * 404 - Não encontrado.
      
      Pessoa com o código informada não se encontra cadastrada.
      
    * 401 - Não autorizado
        
        Token inválido ou expirado.
        
    * 400 - Parâmetros inconsistentes.
      
      Erro ao processar imagem / Tamanho do arquivo superior ao tamanho máximo suportado / Tipo de arquivo inválido
  
    * 403 - Usuário incorreto
      
      Caso o usuário-alvo da operação não seja igual ao usuário da sessão (autenticado).
      

# Perfis
  
  O perfil é a entidade que associa uma pessoa à um aplicativo. O perfil também armazena dados específicos da pessoa que não estão entre os básicos do cadastro da mesma. 

### Buscar perfil 

  Busca o perfil de uma pessoa em determinado aplicativo.
  
* `GET - /rest/pessoas/{codPessoa}/perfil`

  **Parâmetros** 
    
    * appIdentifier - Parâmentro de header. Indica o código do aplicativo onde se irá buscar o perfil.
    * {codPessoa} - Parâmetro de path. Código da pessoa que possui o perfil.
  
  **Retorno**
    
    * 200 - Ok
    
      Retorna dados do perfil.
      
      **Exemplo**
        
        ````
          {
            "camposAdicionais": "escola: 53012607, serie: 3, ano: 2011, grau: 3",
            "tipoPerfil": {
              "codTipoPerfil": 21,
              "descricao": "aluno"
            }
          }
        ```
    * 404 - Não encontrado
      
      Usuário não cadastrado ou Aplicativo não encontrado ou Perfil não encontrado para o usuário no aplicativo.
    
    * 400 - Parâmetros inconsistentes
      
      Parâmetro **appIdentifier** não númerico. 
      
### Cadastrar Perfil 

  Cadastra o perfil de um usuário em determinado aplicativo.
  
* `POST - /rest/pessoas/{codPessoa}/perfil`

  **Parâmetros**
  
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa para qual o perfil será criado.
    
    * **body** - Campos com informações sobre o perfil.
    
      * camposAdicionais - Dados adicionais do perfil. É uma string, logo pode estar em qualquer formato que a aplicação prover. Porém é recomendado usar o formato JSON para uma melhor padronização.
      * tipoPerfil 
        * codTipoPerfil - Código do tipo de perfil que já se encontra cadastrado e associado à um aplicativo.
      
      **Exemplo**
      ```
        {
          "camposAdicionais": "escola: 53012607, serie: 3, ano: 2011, grau: 3",
          "tipoPerfil": {
            "codTipoPerfil": 21,
          }
        }
      ```
   **Retorno** 
    
    * 200 - Cadastrado com sucesso.
    
      Retorna os dados cadastrados do perfil em formato **JSON**.
      
        **Exemplo**
        ```
          {
            "camposAdicionais": "cod: 23",
            "tipoPerfil": {
              "codTipoPerfil": 2,
              "descricao": "Administrador"
            }
          }
        ```
    * 400 - Parâmentros incorretos
    
      Algum parâmetro está inconsistente ou o json está mal formatado. A mensagem de erro vai no corpo da resposta.
    
    * 404 - Não encontrado
      
      Usuário não cadastrado ou tipo de perfil não cadastrado.
      
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
  
### Excluir perfil

  Exclui o perfil de um usuário em determinado aplicativo.
  
* `DELETE - /rest/pessoas/{codPessoa}/perfil`
  
  **Parâmetros**
    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * appIdentifier - Parâmentro de header. Indica o código do aplicativo onde se irá buscar o perfil.
    
    * {codPessoa} - Parâmetro de path. Código da pessoa que possui o perfil que será excluído.
  
   * 200 - Ok
    
      Excluído com sucesso. 

    * 404 - Não encontrado
      
      Usuário não cadastrado ou Aplicativo não encontrado ou Perfil não encontrado para o usuário no aplicativo.
    
    * 400 - Parâmetros inconsistentes
      
      Parâmetro **appIdentifier** não númerico. 
    
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.

### Alterar perfil
  
  Altera os dados de um perfil já cadastrado.
  
* `PUT - /rest/pessoas/{codPessoa}/perfil`

  **Parâmetros**
  
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPessoa} - Parâmetro de path. Indica o código da pessoa para qual o perfil será alterado.
    
    * **body** - Campos com informações sobre o perfil.
    
      * camposAdicionais - Dados adicionais do perfil. É uma string, logo pode estar em qualquer formato que a aplicação prover. Porém é recomendado usar o formato JSON para uma melhor padronização.
      * tipoPerfil 
        * codTipoPerfil - Código do tipo de perfil que já se encontra cadastrado e associado à um aplicativo.
      * verificado - Boleano obrigatório. Indica que a alteração foi verificada.
      
      **Exemplo**
      
      ```
        {
          "camposAdicionais": "escola: 53012607, serie: 3, ano: 2011, grau: 3",
          "tipoPerfil": {
            "codTipoPerfil": 21,
          },
          "verificado": true
        }
      ```
  
 **Retorno** 
  
  * 200 - Alterado com sucesso.
  
  * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.

  * 400 - Parâmentros incorretos
    
      Algum parâmetro está inconsistente ou o json está mal formatado.
      Perfil não associado ao usuário.
    
  * 404 - Não encontrado
      
      Usuário não cadastrado ou tipo de perfil não cadastrado.

# Postagem de pessoa


### Buscar postagens de pessoa

  Busca paginada de postagens de uma determinada pessoa.

* `GET - /rest/pessoas/{codPessoa}/postagens`
  
  **Parâmetros**
    
    * appIdentifier - **Opcional**. 
    * codPessoa - Código da pessoa que seram buscadas as postagens. 
    * pagina - **Opcional**.  Parâmetro de query opcional para uma busca paginada. **Opcional**. Número da página com valor padrão 0.
    * quantidadeDeItens - Parâmetro de query opcional que define o máximo de escolas retornadas na busca. **Opcional**.Valor padrão é 20.
  
  **Retorno**
    
    * 200 - Sucesso.
      
      Dados buscados com sucesso.

      ````
      [{
        "links": [
          {
            "rel": "self",
            "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/302"
          }
        ],
        "codPostagem": 302,
        "dataHoraPostagem": "2016-05-03T15:50:42BRT",
        "conteudos": [
          {
            "links": [
              {
                "rel": "detalhe",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/302/conteudos/267"
              }
            ],
            "codConteudoPostagem": 267
          }
        ],
        "codObjetoDestino": 5301803030121,
        "codTipoObjetoDestino": 100,
        "codTipoPostagem": 105
      }]
      ```
    * 400 - Parâmetros incorretos.
      
      Algum parâmetro está inconsistente.
     
    * 404 - Não encontrado
      
      Usuário com o código enviado não se encontra cadastrado.
    

# Postagens

  A postagem é a entidade mais genérica do metamodelo e que abstrai qualquer informação gerada por um usuário do aplicativo que queria ser armazenada dentro da plataforma. Uma postagem é só a representação básica da entidade, onde o que compõe a mesma são os [**conteúdos**](#conteudos-de-postagens) que podem ser textuais ou arquivos em geral e que serão explicados a seguir. A postagem pode, opcionalmente, estar relacionada à algum objeto e também à uma outra postagem. Um exemplo disso é um modelo de rede social onde se tem um texto publicado e o mesmo possui comentários. Abstraindo isso para o metamodelo, teriamos apenas postagens de tipos diferentes, onde cada comentário em forma de postagem estaria relacionada à uma outra postagem que representa o texto publicado. O relacionamento com objetos funciona com os campos **codObjetoDestino** e **codTipoObjetoDestino**, onde o codTipoObjetoDestino é o código do tipo de objeto que deve estar previamente cadastrado na plataforma e o código do objeto é o identificador único de um objeto qualquer, como por exemplo, uma escola ou estabelecimento de saúde.

### Buscar postagens

   Esse **endpoint** provê buscas de postagens podendo-se filtrar por autor, aplicativo, tipo de postagem, entre outros.

* [`GET - /rest/postagens`] 

  **Parâmetros**
  
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * codAplicativo - Parâmetro de query. **Opcional**. Código do aplicativo do qual serão buscadas as postagens. Caso não seja passado serão retornadas postagens de todos os aplicativos.
    * codAutor - Parâmetro de query. **Opcional**. Código do autor do qual serão buscadas as postagens. Caso não seja passado serão retornadas postagens de todos as pessoas.
    * codPostagemRelacionada - Parâmetro de query. **Opcional**. Código da postagem relacionada da qual serão buscadas as postagens.
    * codTiposPostagem - Parâmetro de query. **Opcional**. Código do tipo de postagem do qual serão buscadas as mesmas. Caso não seja passado serão retornadas postagens de todos os tipos.
    * hashtag - Parâmetro de query. **Opcional**. Hashtag para busca de todas as postagens que possuam como parâmetro texto em algum de seus conteúdos, o texto da hashtag.
    * codTipoObjetoDestino - Parâmetro de query. **Opcional**. Código do tipo de objeto do qual a postagem está relacionada. Caso não seja passado serão buscadas postagens relacionadas à todos tipos os objetos.
    * codObjetoDestino - Parâmetro de query. **Opcional**. Código do objeto do qual a postagem está relacionada. Caso não seja passado serão buscadas postagens relacionadas à todos os objetos.
    * pagina - **Opcional**. Parâmetro de query opcional para uma busca paginada. **Opcional**. Número da página com valor padrão 0.
    * quantidadeDeItens - Parâmetro de query opcional que define o máximo de escolas retornadas na busca. **Opcional**.Valor padrão é 20.
  
  
  **Retorno**  
  
    * 200 - Sucesso.
      
      Dados buscados com sucesso.

      ```
      [{
        "links": [
          {
            "rel": "self",
            "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/302"
          }
        ],
        "codPostagem": 302,
        "dataHoraPostagem": "2016-05-03T15:50:42BRT",
        "conteudos": [
          {
            "links": [
              {
                "rel": "detalhe",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/302/conteudos/267"
              }
            ],
            "codConteudoPostagem": 267
          }
        ],
        "codObjetoDestino": 5301803030121,
        "codTipoObjetoDestino": 100,
        "codTipoPostagem": 105
      }]
      ```
    * 400 - Parâmetros incorretos.
      
      Algum parâmetros está inconsistente.
     
    * 204 - Não encontrado
      
      Nenhuma postagem que se encaixa nos parâmetros passados foi encontrada.
    
  
### Cadastrar Postagem

  Registra uma postagem na plataforma.
  
* `POST - /rest/postagens` 

  **Parâmetros**
  
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * appIdentifier - Parâmtro de header. Código do aplicativo que é dono da postagem.
    
    * **body** - Campos com informações sobre a postagem.
        
      * autor 
        * codPessoa - Código da pessoa que criou a postagem.
      * codObjetoDestino - **Opcional**. Código do objeto à qual a postagem está associada.
      * codTipoObjetoDestino - **Opcional**. Código do tipo de objeto à qual a postagem está relacionada.
      * postagemRelacionada **Opcional**
        * codPostagem - Código da postagem relacionada.
      * tipo 
        * codTipoPostagem - Código do tipo da postagem.
  
      **Exemplo** 
        
        ```
          {
            "autor": {
              "codPessoa": 21
            },
            "codObjetoDestino": 34397294832,
            "codTipoObjetoDestino": 1,
            "postagemRelacionada": {
              "codPostagem": 23
            },
            "tipo": {
              "codTipoPostagem": 100
            }
          }
          
        ```
        
    **Retorno** 
    
    * 201 - Postagem criada com sucesso.
      
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados da postagem no campo **location**. 
          
          ```
            "location": "http://mobile-aceite.tcu.gov.br:80/appCivicoRS/rest/postagens/363"
          ```
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos.
      
    * 404 - Não encontrado
      
      Usuário com o código passado no campo **autor.codPessoa** não foi encontrado ou usuário ou aplicativo não encontrado ou Tipo de objeto destino não cadastrado.  
      
    * 403 - Proibido
      
      Usuário autor da postagem é diferente do usuário dono do token fornecido.
      

### Encontrar Postagem

  Busca dados da postagem pelo código do mesmo.
  
* `GET - /rest/postagens/{codPostagem}` 

  **Parâmetros**
    
     * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPostagem} - Parâmetro de path que indica código da postagem a ser buscada.
    
  **Retorno**
  
    * 200 - 0k
    
        ```
          {
            "links": [
              {
                "rel": "self",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/25/tipos-perfil/41"
              },
              {
                "rel": "aplicativo",
                "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/25"
              }
            ],
            "codTipoPerfil": 41,
            "descricao": "administrador",
            "dataHoraCriacao": "2016-05-29T15:11:00BRT"
          }
        ```
        
    * 404 - Não encontrado.
    
        Não foi encontrado um tipo de perfil com esse código nesse aplicativo.
  
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    
### Excluir Postagem 
  
  Exclui uma postagem e seus conteúdos da plataforma.

* `DELETE - /rest/postagens/{codPostagem}

  **Parâmetros** 
    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPostagem} - Parâmetro de path. Indica o código da postagem a ser excluída.
  
  **Retorno**
    
    * 200 - Ok    
      
      Excluído com sucesso.
      
    * 404 - Não encontrado.
      
      Postagem com o código informada não se encontra cadastrada.

# Avaliações de Objeto

  A entidade de postagem embora genérica, em muitos aplicativos pode ser usada para armazenar avaliações em geral, seja de estabelecimentos de saúde, escolas, entre outros. Para isso o conteúdo da postagem possui um campo numérico chamado **valor**, que é responsáve por armazenar avaliações em uma escala numérica de acordo com a necessidade da aplicação. Esse campo numérico provê a possibilidade da criação de endpoints que sejam especificos para avaliação dentro da postagem, como por exemplo, média de avaliações em um objeto específico, quantidade de avaliações em um objeto específico, entre outros.
  
### Média de Avaliações

  Retorna a média numérica das avaliações em determinado objeto e a quantidade de avaliações feitas. **Obs**: A média será retornada de acordo com os valores dos conteúdos de postagens no campo **valor**.
  
* `GET - /rest/postagens/tipopostagem/{codTipoPostagem}/tipoobjeto/{codTipoObjetoDestino}/objeto/{codObjetoDestino}`

  **Parâmetros** 
  
    * {codTipoPostagem} - Parâmetro de path. Código do tipo da postagem correspondente à avaliação.
    * {codTipoObjetoDestino} - Código do tipo de objeto que será buscado à média e quantidade.
    * {codObjetoDestino} - Código do objeto em que foi feita a avaliação.
  
  **Retorno** 
  
    * 200 - Sucesso
      
      **Exemplo**
      
        ```
          {
            "contagem": 0,
            "media": 0
          }
        ```
        
        * media - Média dos valores contidos no conteúdo das postagens e no campo valor.
        * contagem - Quantidade de avaliações realizadas nesse objeto.
    
    * 400 - Parâmentros incorretos
      
      Algum dos parâmteros não foi passado incorretamente como um campo não numérico.
    
    * 404 - Não encontrado
    
      Não há avaliações ou Tipo de objeto de destino inválido ou Tipo de postagem não cadastrado
      
      
# Conteúdos de Postagens

  Uma postagem pode ser composta por um ou mais conteúdos. Os conteúdos são o corpo da postagem e podem ser apenas textuais ou podem conter arquivos de qualquer extensão. 
  
### Criar conteúdo de postagem

  Cria um conteúdo e associa o mesmo à uma postagem.
  
* `POST - /rest/postagens/{codPostagem}/conteudos`

  **Parâmetros**
  
  **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPostagem} - Parâmetro de path. Código da postagem à qual será associada o conteúdo.
    
    * **body** - Campos com informações do conteúdo.
      
      * JSON - String no formato **JSON** representando o conteúdo.
      * texto - Campo textual usado para associar hashtags à postagem. Para associar uma hashtag à postagem basta colocá-la no campo texto com o caracter '#'. Esse campo também pode ser usado para postagem textual simples sem relação com hashtags, para isso basta apenas não utilizar o caracter '#' no início do mesmo.
      * valor - Campo usado para avaliações em objetos. É recomendado usar esse campo para postagens com o intuito de avaliar algum objeto em uma escala numérica.
    
    **Exemplo** 
      
      ````
        {
          "JSON": "{"campo1" : "valor", "campo2": "valor2"}",
          "texto": "texto",
          "valor": 10
        }
      
      ```
  **Retorno** 
  
    * 201 - Conteúdo adicionado com sucesso.
      
      Retorna no *header* da resposta o link onde se pode ter acesso aos dados cadastrados do conteúdo no campo **location**. 
          
          ```
            http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/302/conteudos/313
          ```
          
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos ou formato do **JSON** incorreto.
      
###  Encontrar conteudo de postagem

  Encontra os dados de um conteúdo pelo código do mesmo.

* `GET - /rest/postagens/{codPostagem}/conteudos/{codConteudo}`

  **Parâmetros**
  
     * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPostagem} - Parâmetro de path. Código da postagem do conteúdo.
    * {codConteudo} - Parâmetro de path. Código do conteúdo a ser buscado.
  
  **Retorno** 
    
    * 200 - 0k
    
        ```
            {
              "codConteudoPost": 271,
              "postagem": {
                "codPostagem": 306,
                "links": [
                  {
                    "rel": "self",
                    "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/306"
                  }
                ]
              },
              "valor": 2,
              "links": [
                {
                  "rel": "self",
                  "href": "http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/postagens/306/conteudos/271"
                }
              ]
            }
        ```
        
    * 404 - Não encontrado.
    
        Não foi encontrado um conteúdo com esse código nessa postagem.
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
### Alterar conteúdo de postagem
  
  Altera um determinado conteúdo de uma postagem.
  
* [`PUT - /rest/postagens/{codPostagem}/conteudos/{codConteudo}`](#alterar-conteúdo-de-postagem)

  **Parâmetros**
    
    **aplication/json**
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPostagem} - Parâmetro de path. Código da postagem do conteúdo.
    * {codConteudo} - Parâmetro de path. Código do conteúdo a ser aterado.
    
    * **body** - Campos com informações do novo conteúdo.
      
      * JSON - String no formato **JSON** representando o conteúdo.
      * texto - Campo textual usado para associar hashtags à postagem. Para associar uma hashtag à postagem basta colocá-la no campo texto com o caracter '#'. Esse campo também pode ser usado para postagem textual simples sem relação com hashtags, para isso basta apenas não utilizar o caracter '#' no início do mesmo.
      * valor - Campo usado para avaliações em objetos. É recomendado usar esse campo para postagens com o intuito de avaliar algum objeto em uma escala numérica.
      
       **Exemplo** 
      
      ````
        {
          "JSON": "{"campo1" : "valor", "campo2": "valor2"}",
          "texto": "texto",
          "valor": 10
        }
      
      ```
  
  **Retorno** 
  
    * 200 - Conteúdo alterado com sucesso.
      
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos.
      
    * 404 - Não encontrado
      
        Não foi encontrado um conteúdo com esse código nessa postagem.
    
### Excluir conteúdo de postagem
  
  Excluí um conteúdo de determinada postagem.
  
* `DELETE - /rest/postagens/{codPostagem}/conteudos/{codConteudo}`

  **Parâmetros** 
    
    * {codPostagem} - Parâmetro de path. Código da postagem do conteúdo.
    * {codConteudo} - Parâmetro de path. Código do conteúdo a ser excluído.
  
  **Retorno** 
  
    * 200 - Conteúdo excluído com sucesso.
      
    * 401 - Não autorizado.
      
      O apptoken enviado não é um token válido ou está expirado.
          
    * 400 - Parâmentros incorretos
      
      Falta de parâmetros obrigatórios ou parâmetros incorretos.
      
    * 404 - Não encontrado
      
        Não foi encontrado um conteúdo com esse código nessa postagem.
    
### Encontrar conteúdo binário de postagem
   
  Busca conteúdo binário de uma postagem.

* `GET - /rest/postagens/{codPostagem}/conteudos/{codConteudo}/conteudoBinario`

  **Parâmteros** 
  
    * {codPostagem} - Parâmetro de path. Código da postagem do conteúdo.
    * {codConteudo} - Parâmetro de path. Código do conteúdo que possui um arquivo binário relacionado.
    
  **Retorno** 
    
    * 200 - Ok
      
      Conteudo binário será retornado.
      
    * 400 - Parâmentros incorretos
      
      Parâmtros de path passados são inválidos.
      
    * 404 - Não encontrado
      
        Não foi encontrado um conteúdo binário com esse código nessa postagem.
    

### Criar conteúdo binário de postagem

  Registra um arquivo como parte de um conteúdo.
  Tamanho máximo do arquivo a ser carregado é de **4MB**.

* `POST - /rest/postagens/{codPostagem}/conteudos/{codConteudo}/conteudoBinario`

  **Parâmetros**
    
    **multipart/form-data**

    
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](#autenticar), e enviado nas requisições subsequentes pela aplicação cliente.
    
    * {codPostagem} - Parâmetro de path. Código da postagem do conteúdo.
    * {codConteudo} - Parâmetro de path. Código do conteúdo em que será associado o arquivo binário.
    
    * file - Arquivo binário que será registrado. Tamanho máximo do arquivo a ser carregado é de **4MB**.
  
  **Retorno**
    
    * 201 - Criado com sucesso
    
      Arquivo foi registrado e associado à postagem.
    
    * 400 - Parâmentros incorretos
      
      Parâmtros de path passados são inválidos.
      
    * 404 - Não encontrado
      
        Não foi encontrado um conteúdo com esse código nessa postagem.
        

# Tipos de Postagem 

  Tipos de postagem descrevem o que significa cada postagem.
  
### Buscar tipos de postagem

* [`GET - /rest/tipos-postagem`]

### Registrar tipo de objeto
  
* [`POST - /rest/tipos-postagem`]

### Encontrar tipo de objeto

* [`GET - /rest/tipos-postagem/{codTipoObjeto}`]

### Alterar tipo de objeto

* [`PUT - /rest/tipos-postagem/{codTipoObjeto}`]
  
  
