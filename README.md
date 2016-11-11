# AppCivico / Nuvem Cívica
Documentação de Endpoints para acesso à plataforma de AppCivicos do TCU.
 - Para dúvidas ou esclarecimentos sobre o uso da plataforma, utilize a [página de Issues do repositório.](https://github.com/AppCivicoPlataforma/AppCivico/issues)
 - Temos uma página de [FAQ na Wiki](https://github.com/AppCivicoPlataforma/AppCivico/wiki/%5BFAQ%5D-Perguntas-Frequentes) para documentar perguntas frequentes e dicas.
 - Após o término do Desafio de Aplicativos Cívicos, iniciaremos uma evolução da plataforma para sua versão 2.0. As alterações futuras podem ser visualizadas na [página do projeto AppCivico Versão 2.0](https://github.com/AppCivicoPlataforma/AppCivico/projects/1) deste repositório.

## Dados Abertos
Visando facilitar o acesso à dados abertos do governo para a comunidade de desenvolvedores o Tribunal de Contas da União criou a plataforma AppCívico, que fornece através de uma API de serviços REST informações abertas. Exemplo:
- Informações georreferênciadas sobre estabelecimentos de saúde públicos e privados do país, sendo as mesmas providas do   [Cadastro Nacional de Estabelecimentos de Saúde (CNES)](http://cnes.datasus.gov.br/) que é a base do próprio DataSUS.
- Informações também georreferênciadas sobre escolas públicas e privadas do país providas do Censo Escolar [Instituto      Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira (INEP)](http://portal.inep.gov.br/).
- Informações sobre remédios fabricados no Brasil providas da [Agência Nacional de Vigilância Sanitária](http://portal.anvisa.gov.br/).
- Entre outros dados de utilidade pública.

O objetivo é fazer com que mais desenvolvedores, interessados em desenvolver aplicações cívico sociais possam ter acesso de maneira fácil à dados abertos, gerando cada vez mais aplicações de utilidade pública, que poderão prover tranparência das informações e de certa forma ajudar a população.

## Metamodelo
   Desenvolvedores de aplicativos móveis engajados em causas de cunho cívico ou social, interessados em se lançar em projetos de utilidade pública, muitas vezes esbarram em dificuldades que complicam ou até inviabilizam seus projetos. Entre os problemas mais frequentes estão o custo de serviços de *cloud* e a dificuldade de se desenvolver um serviço de *backend*, em geral webservices REST, para armazenamento de dados da sua aplicação. O desenvolvedor que se interessa por aplicações de cunho cívico social ou de utilidade pública costuma não visar lucro, trabalha individualmente ou em pequenos grupos, e por isso tem dificuldade em arcar com os custos de hospedagem de dados ou de um serviço de *cloud*. Além desse problema com os custos, existe a esforço de desenvolvimento desses serviços. Contruir um serviço em *cloud* para servir de *backend* para uma aplicação é uma tarefa a mais que o desenvolvedor tem no processo de contrução da aplicação e que muitas vezes consome até mais tempo do que o desenvolvimento da própria aplicação.
  
  Pensando nisso a plataforma AppCívico, também chamada de Nuvem Cívica, disponibiliza um conjunto de serviços concebidos como uma abstração de um metamodelo genérico, que se propõe a prover serviços básicos para qualquer aplicativo móvel típico. O metamodelo provê serviços como cadastro e armazenamento de usuários, criação de perfis específicos para determinado aplicativo , *login* com senha ou com redes sociais **Facebook**, **Twitter**, **Intagram** e **GooglePlus**. Além de dar suporte à dados de usuários o metamodelo também proporciona a criação de grupos de usuário relacionados a um aplicativo, provê também suporte à notificações para aplicativos móveis. Para armazenamento de dados bastante genéricos é dado ao desenvolvedor o objeto de **Postagem** onde criada uma postagem, pode - se associar vários conteúdos a mesma seja ele objetos da aplicação ou arquivos binários como por exemplo fotos ou vídeos. Os conteúdos que são objetos objetos são salvos como no formato **JSON**, fazendo com que ele seja dinâmico e genérico podendo armazenar qualquer objeto. Podendo posteriormente alterar, excluir e fazer buscas nos mesmos. A seguir iremos abordar cada *endpoint* do metamodelo especificando como funciona, como cada entidade se relaciona e como usa - lo na sua aplição. Umas das grandes utilidades desse metamodelo, além de facilitar o trabalho do desenvolvedor é contribuir a geração de informação aberta e dados de utilidade pública que podem ajudar a população e contribuir para que os dados abertos se tornem mais precisos. Um exemplo dessa geração de informação, são aplicativos que já usam a base de estabelecimentos de saúde e de escolas, e que por meio de uma mecânica colaborativa o usuário pode dar *feedback* na localização do local, dando assim sugestões de onde seria a localização correta, o que ajuda a tornar a qualidade da informação melhor o que faz com que os aplicativos construidos a partir dessa informação, consigam ser mais efetivos no dia-a-dia da população que utiliza os mesmo.

##API Reference
  Links para Documentação das API
  
  [API de Estabelecimentos de Saúde](/EstabelecimentosAPI.md)
  
  [API de Escolas](/EscolasAPI.md)
  
  [API do Metamodelo](/MetamodeloAPI.md)
  
  [API de Centros de Referência de Assistência Social (CRAS)](/EstabelecimentosAPI.md#postos-de-atendimento-do-centros-de-referência-de-assistência-social)
  
  [API de Centros de Referência Especializado de Assistência Social - Creas](/EstabelecimentosAPI.md#postos-de-atendimento-do-centro-de-referência-especializado-de-assistência-social)
  
  [API de Postos do Site Nacional de Empregos](/EstabelecimentosAPI.md#postos-do-sine)

### Links úteis

- [Faça aqui o download do edital retificado do Desafio](http://portal.tcu.gov.br/lumis/portal/file/fileDownload.jsp?fileId=8A8182A157C4E4100157D381E2BA1CF5)
 
- [Acesse aqui o Gihub da Nuvem Cívica para obter informações técnicas.](https://github.com/AppCivicoPlataforma/AppCivico)
 
- [Acesse aqui a página de cadastramento de desenvolvedor e aplicativo na Nuvem Cívica.](http://mobile-aceite.tcu.gov.br/appCivicoWeb/web/externo/#/login)
 
- [Leia aqui com atenção os procedimentos para o envio das propostas](http://drive.google.com/open?id=0B-NBmgxn2OjNQjR1SEdJaUxLZHM)

### Datas Importantes
|  Evento	| Data |
|-------------------------	|----------------	
| Lançamento do edital    	| 17/08/2016    
| Envio dos aplicativos   	| Até 15/11/2016
| Publicação do resultado 	| Até 22/11/2016 	
| Cerimônia de premiação  	| 29/11/2016     

### Premiação
| Colocação | Valor |
|-------------------------	|----------------
|1º lugar	|R$ 25.000,00
|2º lugar	|R$ 15.000,00
