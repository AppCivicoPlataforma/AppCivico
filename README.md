# AppCivico
Documentação de Endpoints para acesso à plataforma de AppCivicos do TCU.
## Dados Abertos
Visando facilitar o acesso à dados abertos do governo para a comunidade de desenvolvedores o Tribunal de Contas da União criou a plataforma AppCívico, que fornece através de uma API de serviços REST informações abertas. Exemplo:
- Informações georreferênciadas sobre estabelecimentos de saúde públicos e privados do país, sendo as mesmas providas do   [Cadastro Nacional de Estabelecimentos de Saúde (CNES)](http://cnes.datasus.gov.br/) que é a base do próprio DataSUS.
- Informações também georreferênciadas sobre escolas públicas e privadas do país providas do Censo Escolar [Instituto      Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira (INEP)](http://portal.inep.gov.br/).
- Informações sobre remédios fabricados no Brasil providas da [Agência Nacional de Vigilância Sanitária](http://portal.anvisa.gov.br/).
- Entre outros dados de utilidade pública.

O objetivo é fazer com que mais desenvolvedores, interessados em desenvolver aplicações cívico sociais possam ter acesso de maneira fácil à dados abertos, gerando cada vez mais aplicações de utilidade pública, que poderão prover tranparência das informações e de certa forma ajudar a população.

## Metamodelo
  Muitos desenvolvedores na comunidade que tem idéias de aplicações de utilidade pública, muitas vezes esbarram em vários problemas que acabam atrapalhando o desenvolvimento. Alguns dos maiores problemas encontrados são o custo de serviços de *cloud* e a dificuldade de se desenvolver um serviço de *backend*, em geral webservices REST, para armazenamento de dados da sua aplicação. Desenvolver uma aplicação de cívico social de utilidade não visa lucro, então o desenvolvedor acaba não tendo como arcar com os custos de uma hospedagem ou de um serviço de *cloud* e a aplicação acaba não sendo desenvolvida por causa disso. Além desse problema com os custos, existe a parte do desenvolvimento desse serviço. Contruir um serviço em *cloud* para servir de *backend* para uma aplicação é uma tarefa a mais que o desenvolvedor tem no processo de contrução da aplicação e que muitas vezes consome até mais tempo do que o desenvolvimento da própria aplicação.
  
  Para isso a plataforma AppCívico disponibiliza conjunto de serviços que são a abstração de um metamodelo genérico que visa conseguir atender a demanda de aplicações. 

