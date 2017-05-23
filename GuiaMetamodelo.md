Primeiros passos
===================

A **Nuvem Cívica** permite que você obtenha dados abertos de bases públicas de **saúde e educação**, assim como disponibiliza um sistema de **armazenamento de dados estruturado** para sua aplicação. Vamos explicar passo a passo nesse tutorial os procedimentos iniciais para utilização da API.

----------

### Pré-requisitos
----------

#### Cadastro na Nuvem Cívica
Antes de começar, você precisará se cadastrar no Portal do Desenvolvedor da Nuvem Cívica e registrar sua aplicação.

 1. Acesse o [Portal do Desenvolvedor](http://mobile-aceite.tcu.gov.br/appCivicoWeb/web/externo/#/login), e clique na opção **Cadastrar**.
 2. Preencha todos os dados corretamente e confirme os termos de compromisso. 
 3. Após o cadastro, acesse a aba **Aplicativos** no canto superior esquerdo da tela.
 4. Clique em **Novo Aplicativo** e insira o nome e descrição de sua aplicação, e clique em **Cadastrar**.

Você receberá o código identificador do seu aplicativo. ***Lembre-se desse número!*** Ele será necessário em algumas operações da API.

Após esses passos, você já está cadastrado na Nuvem Cívica! Agora, é possível executar operações na API que necessitam de autenticação.

#### Exemplo

 - Cadastrando aplicativo "NovoAplicativo"

> **"Aplicativo cadastrado com sucesso com sucesso. O código do aplicativo é o "448". Esse será o código que você irá usar como parâmetro nos endpoints da plataforma."**

Já podemos fazer nossa primeira requisição! Ao executar a seguinte chamada:
>**http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/aplicativos/448**

Podemos obter as informações básicas referentes ao aplicativo cadastrado, com o seguinte retorno:

```json
{
  "cod": 448,
  "nome": "NovoAplicativo",
  "descricao": "Novo aplicativo teste",
  "links": [
    {
      "rel": "self",
      "href": "http:\/\/mobile-aceite.tcu.gov.br\/appCivicoRS\/rest\/aplicativos\/448"
    },
    {
      "rel": "responsavel",
      "href": "http:\/\/mobile-aceite.tcu.gov.br\/appCivicoRS\/rest\/pessoas\/2"
    }
  ]
}
```

----------

Autenticação
-------------------
Sua aplicação provavelmente precisa saber a identidade de um usuário, para que seja possível salvar seus dados de maneira segura e fornecer acesso aos dados em todos os dispositivos desse usuário. 

O sistema de autenticação da Nuvem Cívica fornece serviços de *backend* prontos para serem utilizados pela sua aplicação, com suporte a cadastro, atualização de dados, recuperação de senha e autenticação segura.


#### Autenticando um usuário
Como fizemos o cadastro no Portal do Desenvolvedor nas etapas anteriores, já é possível se autenticar na Nuvem Cívica utilizando as credenciais fornecidos no momento do cadastro. 

Essa autenticação retorna um ***token*** de acesso em seu cabeçalho, que é necessário em várias operações da API. A URL da requisição de autenticação é a seguinte:

> GET `http://mobile-aceite.tcu.gov.br/appCivicoRS/rest/pessoas/autenticar`
> [(Ver documentação)](https://github.com/AppCivicoPlataforma/AppCivico/blob/master/MetamodeloAPI.md#autenticar)

As credenciais devem ser enviadas via *header*, para evitar chamadas textuais que contenham senha sejam expostas. 

É obrigatório especificar o email do usuário, e é possível escolher entre senha ou token de rede social para a autenticação (dependendo do tipo de cadastro executado). 

##### Exemplo
Para autenticar um usuário teste de credenciais:

 - Email: teste23@tcu.gov.br
 - Senha: "teste"

Deve ser executada a seguinte chamada, informando as credenciais via *header*:

```shell
curl -i -H "email:teste23@tcu.gov.br" -H "senha:teste" -X GET http://mobile-aceite.tcu.gov.br:80/appCivicoRS/rest/pessoas/autenticar

```

> Obs: Exemplo utilizando o comando ``curl`` disponível via terminal. O framework de requisição HTTP deve ser escolhido de acordo com a plataforma/linguagem da sua aplicação.

##### Retorno
O comando acima retorna o seguinte resultado no corpo da resposta:

```json
{
  "nomeUsuario": "Teste23",
  "cod": 4317,
  "email": "teste23@tcu.gov.br",
  "emailVerificado": false,
  "links": [
    {
      "rel": "self",
      "href": "http:\/\/mobile-aceite.tcu.gov.br\/appCivicoRS\/rest\/pessoas\/4317"
    }
  ]
}
```

E no seu *header*:

```http
Date: Thu, 18 May 2017 18:08:27 GMT
Server: Apache-Coyote/1.1
Access-Control-Allow-Headers: Content-Type
Access-Control-Allow-Headers: email, senha, senhaAtual, novaSenha, credencial
Access-Control-Allow-Headers: appToken, appIdentifier, facebookToken, googleToke
Access-Control-Expose-Headers: appToken, Location
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
Access-Control-Allow-Origin: *
appToken: v1_6E8EACCC6B06AC2D08829E2B6917397FC24E0C4CD33E01CC2B90DE16F25EF98288F43E80FADF857C52EDE57AE7633A1A8356D36DD88F89C2AF0D9D846C1F843B099FACA8C6E398DD6B49F28AA4EC8BF80258CB5C2B02AA45B4B07043091B365D9D33747C06C14B7C50FCEE0DAA573D
Content-Type: application/json;charset=UTF-8

```

O campo "**appToken**" informa o *token* de acesso do usuário autenticado. Na documentação, ao se referir a esse campo, o mesmo termo será utilizado.

#### Cadastrando um usuário

Com sua aplicação registrada na Nuvem Cívica e os conhecimentos básicos de autenticação, você já pode implementar o cadastro de usuários no seu programa e desfrutar dos serviços disponibilizados pelo TCU.

Além de um email e senha (parâmetros obrigatórios), é possível informar outros parâmetros informativos no momento do cadastro como sexo, localização, *tokens* de redes sociais e outros.

Para uma referência completa da documentação do *endpoint* de cadastro de usuário, [clique aqui.](https://github.com/AppCivicoPlataforma/AppCivico/blob/master/MetamodeloAPI.md#cadastrar-pessoa)

Metamodelo
-------------------

-------------------


### Algum endpoint do metamodelo não está funcionando corretamente?

Se você percebeu algum problema em um dos webservices do metamodelo ou no [Portal do Desenvolvedor](http://mobile-aceite.tcu.gov.br/appCivicoWeb/web/externo/#/), por favor verifique na sessão de [*issues*](https://github.com/AppCivicoPlataforma/AppCivico/issues) se há algo à respeito. Se não houver, registre seu problema para que possamos verificar e dar um retorno assim que possível. 

### Alguma parte da documentação ficou faltando ou não ficou clara?

Você poderá colaborar com a documentação editando os arquivos e fazendo pull request para que possamos melhorar cada vez mais a plataforma. A sua colaboração é muito importante, pois ajuda na melhoria do da plataforma.

### Alguma sugestão ?

Se tiver alguma sugestão de melhoria nos serviços, dê seu *feedback* através do e-mail [appcivico@tcu.gov.br](mailto:appcivico@tcu.gov.br). 

### Sou um Desenvolvedor iOS

Para desenvolvedores iOS existe uma framework com métodos de conveniência para acesso aos endpoints do metamodelo.
O framework não está completo, porém você pode colaborar no desenvolvimento e na melhora do mesmo. 
Clique aqui para acessar o repositório do [APCSDK](https://github.com/neneds/APCSDK2).

