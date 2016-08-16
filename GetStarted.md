# AppCivico / Nuvem Cívica


## Como usar o metamodelo nos meus aplicativos?

Para utilizar a API do metamodelo da Nuvem Cívica, primeiramente é necessário se cadastrar como desenvolvedor,
para que assim você possa criar aplicativos e começar a usar os recursos disponíveis.

Você poderá realizar o seu cadastro através do [Portal do Desenvolvedor](http://mobile-aceite.tcu.gov.br/appCivicoWeb/web/externo/#/login){:target="_blank"}. 
Você cadastrará algumas informações sobre você e sua carreira como desenvolvedor, falando um pouco de sua experiência com desenvolvimento de aplicativos móveis. 

Se você já possui cadastro seja no [Portal](http://mobile-aceite.tcu.gov.br/appCivicoWeb/web/externo/#/login){:target="_blank"} ou em algum aplicativo que utiliza a API do metamodelo, você poderá irá apenas fazer sua autenticação e acessar a plataforma.

Com o seu perfil cadastrado, você terá acesso ao Portal do Desenvolvedor, que é um site onde você poderá criar e gerênciar seus aplicativos, tipos de perfil para os mesmos e tipos de postagem que serão registradas. 

### Aplicativos

* Para cada aplicativo criado, será gerado um código, que será usado por você nas chamadas das API's do metamodelo. Esse código é muito importante, é com ele que você irá registrar e buscar postagens, grupos, instalações e notificações dentro da plataforma. Para mais informações acesse a sessão de [Aplicativos](/MetamodeloAPI.md/#aplicativos) na documentação do metamodelo.

### Tipo de Perfil

* Para cada um de seus aplicativos, você poderá criar vários tipos de perfil. O tipo de perfil, é o que fará a destinção entre usuários dentro do seu aplicativo. Para mais informações acesse a sessão de [Tipos de Perfil](/MetamodeloAPI.md/#tipos-de-perfil) na documentação do metamodelo.


### Tipos de Postagem

* Postagens são a base de armazenamento de informação genérica dentro do metamodelo. Para distiguir as informações armazenadas em formato de postagem, cada uma delas possui um tipo. Você pode criar quantos tipos de postagem forem necessárias para seu aplicativo. Você pode configurar as seguintes características em um tipo de postagem:
    * Tipo de postagem pai, que é o tipo de postagem associada. 
    * Um tipo de objeto relacionado, que pode um dos objetos já pré cadastrados. São os dados abertos disponibilizados como por exemplo, estabelecimentos de saúde, escolas, remédios, entre outros.
    * Descrição simples e descrição detalhada dos campos e dados que serão armazenados nas postagens desse tipo.
    
Para mais informações acesse a sessão de [Tipos de Postagem](/MetamodeloAPI.md/#tipos-de-postagem) na documentação do metamodelo.

### Hashtags

* Hashtags são marcadores em postagens, e você pode definir suas hastags por aplicativo ou seus usuários podem usar as hashtags pré-definidas na nuvem cívica. Para mandar uma postagem com hastags um dos conteúdos da mesma deve possuir uma hashtag pré-definida no campo texto.  

Para mais informações acesse a sessão de [Hashtags](/MetamodeloAPI.md/#hashtags) na documentação do metamodelo.

## Algum end-point do metamodelo não está funcionando corretamente?

Se você percebeu algum problema em um dos webservices do metamodelo ou no [Portal do Desenvolvedor](http://mobile-aceite.tcu.gov.br/appCivicoWeb/web/externo/#/), por favor verifique na sessão de [*issues*](https://github.com/AppCivicoPlataforma/AppCivico/issues) se há algo à respeito. Se não houver, registre seu problema para que possamos verificar e dar um retorno assim que possível. 

## Alguma parte da documentação ficou faltando ou não ficou clara?

Você poderá colaborar com a documentação editando os arquivos e fazendo pull request para que possamos melhorar cada vez mais a plataforma. A sua colaboração é muito importante, pois ajuda na melhoria do da plataforma.

## Alguma sugestão ?

Se tiver alguma sugestão de melhoria nos serviços, dê seu *feedback* através do e-mail [appcivico@tcu.gov.br](mailto:appcivico@tcu.gov.br). 



