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
* [`GET - /rest/grupos/{codGrupo}/membros`](#membros-por-grupo)
* [`POST - /rest/grupos/{codGrupo}/membros`](#adicionar-membro-em-grupo)
* [`GET - /rest/grupos/{codGrupo}/membros/{codMembro}`](#encontrar-membro-em-grupo)

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
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](), e enviado nas requisições subsequentes pela aplicação cliente.
      
    * **body** - Campos com informações sobre o aplicativo.
      
        * codResponsavel - Código do desenvolvedor responsável pelo aplicativo.
        * descricao - Breve descrição do aplicativo. Explicação sobre o que o aplicativo faz, qual àrea de abordagem, e sobre que tipo de informação esse aplicativo armazena na plataforma.
        * nome - Nome do aplicativo.
        * token - . **Opcional**
        
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
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](), e enviado nas requisições subsequentes pela aplicação cliente.
    
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
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](), e enviado nas requisições subsequentes pela aplicação cliente.
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
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](), e enviado nas requisições subsequentes pela aplicação cliente.
      
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
      
    * appToken - Parâmtro de header. Token para autenticação de sessão. Obtido inicialmente por meio da operação [`GET - /rest/pessoas/autenticar`](), e enviado nas requisições subsequentes pela aplicação cliente.
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
  * 404 - Aplicativo não encontrado
  
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
      
  
