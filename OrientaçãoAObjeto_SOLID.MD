# Orientação a Objeto – SOLID

## O que é SOLID?

SOLID é um acrônimo dos cinco primeiros princípios da programação orientada a objetos e design de código identificados por Robert C. Martin (ou Uncle Bob) por volta do ano 2000. O acrônimo SOLID foi introduzido por Michael Feathers, após observar que os cinco princípios poderiam se encaixar nesta palavra.

São eles:

| Letra | 	Sigla	| Nome	| Definição | 
|---|---|---|---| 
| S	|  SRP	| Principio da Responsabilidade Única	Uma classe deve ter um, e somente um, motivo para mudar.| 
| O	|  OCP	| Princípio Aberto-Fechado	Você deve ser capaz de estender um comportamento de uma classe, sem modificá-lo.| 
| L	 | LSP	| Princípio da Substituição de Liskov	As classes base devem ser substituíveis por suas classes derivadas.| 
| I	 | ISP	| Princípio da Segregação da Interface	Muitas interfaces específicas são melhores do que uma interface única.| 
| D	 | DIP	| Princípio da inversão da dependência	Dependa de uma abstração e não de uma implementação.| 

Os princípios SOLID devem ser aplicados para se obter os benefícios da orientação a objetos, tais como:

- Seja fácil de se manter, adaptar e se ajustar às alterações de escopo;
- Seja testável e de fácil entendimento;
- Seja extensível para alterações com o menor esforço necessário;
- Que forneça o máximo de reaproveitamento;
- Que permaneça o máximo de tempo possível em utilização.

### Utilizando os princípios SOLID é possível evitar problemas muito comuns:

- Dificuldade na testabilidade / criação de testes de unidade;
- Código macarrônico, sem estrutura ou padrão;
- Dificuldades de isolar funcionalidades;
- Duplicação de código, uma alteração precisa ser feita em N pontos;
- Fragilidade, o código quebra facilmente em vários pontos após alguma mudança.

Os princípios SOLID deveriam ser aplicados por qualquer desenvolvedor maduro, porém pouquíssimos profissionais preocupam-se em utilizá-los, sugiro que crie um sistema simples e utilize estes princípios para treinar, será uma experiência gratificante.

Este é apenas o artigo introdutório sobre SOLID, nos próximos abordarei cada princípio em um artigo separadamente, explicando e demonstrando com código e exemplos a proposta de cada um, continue acompanhando