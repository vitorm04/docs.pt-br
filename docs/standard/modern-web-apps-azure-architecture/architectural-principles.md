---
title: "Princípios de arquitetura"
description: "Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Princípios de arquitetura"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bdb215d64253fb7d22ae2c5648030336850006b5
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="architectural-principles"></a>Princípios de arquitetura

> "Se construtores criados edifícios os programadores de maneira gravou programas, o primeiro woodpecker que surgirem seria destruir civilização."  
> _\- Gerald Weinberg_

## <a name="summary"></a>Resumo

Você deve projetar e criar soluções de software com facilidade de manutenção em mente. Os princípios descritos nesta seção podem ajudar a orientar você em direção à arquitetura decisões que resultam em aplicativos de limpo e sustentáveis. Em geral, esses princípios vai guiá-lo para criar aplicativos fora de componentes individuais que não estejam firmemente acoplados a outras partes do seu aplicativo, mas em vez disso, se comunicam através de interfaces explícitas ou sistemas de mensagens.

## <a name="common-design-principles"></a>Princípios de design comum

### <a name="separation-of-concerns"></a>Separação de preocupações

É um princípio orientador ao desenvolver **separação de preocupações**. Esse princípio declarações com base nos tipos de trabalho, que ele executa a que o software deve ser separado. Por exemplo, considere um aplicativo que inclui a lógica para identificar notáveis itens a serem exibidos ao usuário, e que formata esses itens de uma maneira específica para torná-los mais notável. O comportamento é responsável por escolher quais itens devem ser de formato devem ser mantidos separados do comportamento responsável por formatação dos itens, como eles são separadas preocupações somente Coincidentemente relacionados uns aos outros.

Em termos de arquitetura, aplicativos podem ser criados logicamente para seguir esse princípio, separando o comportamento de negócios principal da lógica de interface de usuário e infraestrutura. Idealmente, lógica e regras de negócio devem residir em um projeto separado, que não deve depender de outros projetos no aplicativo. Isso ajuda a garantir que o modelo de negócios é fácil de testar e pode evoluir sem sendo acoplado detalhes de implementação de nível inferior. Separação de preocupações é uma consideração importante por trás do uso de camadas em arquiteturas de aplicativo.

### <a name="encapsulation"></a>Encapsulamento

Diferentes partes de um aplicativo devem usar **encapsulamento** isolá-los de outras partes do aplicativo. Camadas e componentes de aplicativo devem ser capazes de ajustar sua implementação interna sem quebrar seus parceiros, como contratos externos não forem violados. Uso adequado de encapsulamento ajuda a alcançar um acoplamento flexível e modularidade em projetos de aplicativo, como pacotes e objetos podem ser substituídos com implementações alternativas, contanto que a mesma interface é mantida.

Em classes, encapsulamento é obtido por meio da limitação fora do access para o estado interno da classe. Se quiser que um ator externo manipular o estado do objeto, ele deve fazer isso por meio de uma função bem definida (ou o setter da propriedade), em vez de ter acesso direto ao estado particular do objeto. Da mesma forma, os componentes de aplicativos e os próprios aplicativos devem expor interfaces bem definidas para seus colaboradores para uso, em vez de permitir que seu estado a ser modificado diretamente. Isso libera internas de design do aplicativo a evolução ao longo do tempo sem se preocupar que fazer assim será interrompido colaboradores, desde que os contratos públicos são mantidos.

### <a name="dependency-inversion"></a>Inversão de dependência

A direção de dependência dentro do aplicativo deve ser na direção de abstração, não os detalhes de implementação. A maioria dos aplicativos são gravados, de modo que os fluxos de dependência de tempo de compilação na direção da execução de tempo de execução. Isso produz um gráfico de dependência direta. Ou seja, se as chamadas de módulo A uma função no módulo B, que chama uma função em um módulo C e à vontade de tempo A compilação dependem B que dependerá C, conforme mostrado na Figura 4-1.

![](./media/image4-1.png)

**Figura 4-1.** Gráfico de dependência direta.

Aplicando o princípio de inversão de dependência permite A para chamar métodos em uma abstração que implementa B, tornando possível para A chamada B em tempo de execução, mas para B depende de uma interface controlada por um em tempo de compilação (portanto, *invertendo* a típica tempo de compilação dependência). Em tempo de execução, o fluxo de execução do programa permanece inalterado, mas a introdução de interfaces significa que diferentes implementações de interfaces podem ser conectadas facilmente.

![](./media/image4-2.png)

**Figura 4-2.** Gráfico de dependência invertido.

**Inversão de dependência** é uma parte importante da criação de aplicativos acoplados de forma flexível, desde que os detalhes de implementação podem ser gravados dependem e implementar abstrações de nível superior, em vez do oposto. Os aplicativos resultantes são mais testável, modular e sustentável como resultado. A prática de *injeção de dependência* se tornou possível pelo seguir o princípio de inversão de dependência.

### <a name="explicit-dependencies"></a>Dependências explícitas

**Classes e métodos devem exigir explicitamente os objetos de colaboração que precisam para funcionar corretamente.** Construtores da classe oferecem uma oportunidade para classes identificar os itens que precisam para estar em um estado válido e funcione corretamente. Se você definir as classes que podem ser construídos e chamado, mas que só funcionará corretamente se certos componentes de infraestrutura ou global estão em vigor, essas classes estão sendo *desonestos* com seus clientes. O contrato de construtor está informando que ele precisa apenas os itens especificados (possivelmente nada se a classe está usando apenas um construtor padrão), mas em seguida, em tempo de execução acontece o objeto cliente realmente precisava de outra coisa.

Seguindo o princípio de dependência explícita, seus métodos e classes estão sendo honestos com seus clientes sobre o que precisam para funcionar. Isso faz com que seu código autodescritivo mais e a codificação contratos mais amigável, desde que os usuários irão confiar que, desde que eles fornecem o que é exigido na forma de método ou irão se comportar os parâmetros do construtor, os objetos que estão trabalhando com corretamente em tempo de execução.

### <a name="single-responsibility"></a>Responsabilidade único

O princípio da responsabilidade única se aplica ao design orientado a objeto, mas também pode ser considerado como um princípio de arquitetura semelhante a separação de preocupações. Ele informa que objetos devem ter apenas uma responsabilidade e que eles devem ter apenas um dos motivos para alterar. Especificamente, a única situação na qual o objeto deve alterar é se a maneira na qual ele executa sua um responsabilidade deve ser atualizada. Esse princípio a seguir ajuda a produzir mais flexível e sistemas modulares, pois muitos tipos de novo comportamento podem ser implementados como novas classes, em vez de pela adição de responsabilidade adicional para as classes existentes. Adicionar novas classes sempre é mais segura do que alterar as classes existentes, desde que nenhum código ainda depende das novas classes.

Em um aplicativo monolítico, podemos aplicar o princípio da responsabilidade única em um alto nível para as camadas do aplicativo. Responsabilidade de apresentação deve permanecer no projeto de interface do usuário, enquanto o acesso a dados responsabilidade deve ser mantida em um projeto de infra-estrutura. Lógica de negócios deve ser mantida no projeto de núcleo do aplicativo, onde ele pode ser facilmente testado e pode evoluir independentemente de outras responsabilidades.

Quando esse princípio é aplicado a arquitetura do aplicativo e levado para seu ponto de extremidade lógico, você obtém microservices. Um determinado microsserviço deve ter uma única responsabilidade. Se você precisar estender o comportamento de um sistema, é melhor fazê-lo adicionando microservices adicionais, em vez de pela adição de responsabilidade de um existente.

[Saiba mais sobre a arquitetura de microservices](http://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Não repetitivo (SECA)

O aplicativo deve evitar especificar o comportamento relacionado a um determinado conceito em vários locais, pois esta é uma fonte frequente de erros. Em algum momento, uma alteração nos requisitos exigirá alterar esse comportamento e a probabilidade de que pelo menos uma instância do comportamento não conseguirão ser atualizados resultará em um comportamento inconsistente do sistema.

Em vez de duplicar a lógica, encapsulá-lo em uma construção de programação. Faça isso construir a autoridade única sobre esse comportamento e ter qualquer outra parte do aplicativo que requer esse comportamento, use a nova construção.

> [!NOTE]
> Evite juntos associação comportamento só é Coincidentemente repetitivo. Por exemplo, só porque duas constantes diferentes ambos têm o mesmo valor, isso não significa que você deve ter apenas uma constante, quando conceitualmente está se referindo a coisas diferentes.

### <a name="persistence-ignorance"></a>Ignorância de persistência

**Ignorância de persistência** (PI) refere-se aos tipos que precisam ser mantidos, mas cujo código é afetado pela opção de tecnologia de persistência. Esses tipos de .NET às vezes são chamados de Plain Old CLR Objects (POCOs), pois eles não precisam para herdar de uma classe base específica ou implementar uma interface específica. Ignorância de persistência é importante porque ele permite que o mesmo modelo de negócios ser persistente de várias maneiras, oferecendo flexibilidade adicional para o aplicativo. Opções de persistência podem ser alterados ao longo do tempo, de tecnologia de um banco de dados para outro, ou outras formas de persistência podem ser necessárias além do que o aplicativo foi iniciado com (por exemplo, usando um cache Redis ou DocumentDb do Azure além um banco de dados relacional).

Alguns exemplos de violações desse princípio incluem:

-   Uma classe base necessária

-   Uma implementação de interface necessária

-   Classes responsáveis por salvar si (como o padrão de registro ativo)

-   Construtor padrão necessário

-   Propriedades que exigem a palavra-chave virtual

-   Atributos necessários específicos de persistência

O requisito de classes que qualquer um dos recursos ou comportamentos acima adiciona acoplamento entre os tipos para ser persistente e a opção de tecnologia de persistência, dificultando a adotar novas estratégias de acesso de dados no futuro.

### <a name="bounded-contexts"></a>Contextos limitados

**Limitado contextos** são um padrão central no Design Domain-Driven. Eles fornecem uma maneira de complexidade lidando com aplicativos grandes ou organizações por dividi-lo em módulos conceituais separados. Cada módulo conceitual, em seguida, representa um contexto que é separado de outros contextos (portanto, limitado) e pode evoluir independentemente. Cada contexto associado deve ser o ideal é livre para escolher seus próprios nomes de conceitos dentro dele e deve ter acesso exclusivo ao seu próprio repositório de persistência.

No mínimo, aplicativos web individuais devem tentar ser seu próprio contexto limitado, com seu próprio repositório de persistência para seu modelo de negócios, em vez de compartilhar um banco de dados com outros aplicativos. Comunicação entre contextos limitadas ocorre por meio de interfaces programáticas, em vez de por meio de um banco de dados compartilhado, o que permite que a lógica de negócios e eventos sejam ocorram em resposta a alterações que ocorrem. Limitada contextos mapa atentamente para microservices, que também idealmente são implementados como seus próprios contextos limitados individuais.

> ### <a name="references--modern-web-applications"></a>Referências – aplicativos Web modernos
> - Separação de preocupações  
> <http://deviq.com/separation-of-concerns/>
> - **Encapsulation** <http://deviq.com/encapsulation/>
> - **Princípio de inversão de dependência**  
> <http://deviq.com/dependency-inversion-principle/>
> - **Princípio de Dependências Explícitas**  
> <http://deviq.com/explicit-dependencies-principle/>
> - **Não repetitivo**  
> <http://deviq.com/don-t-repeat-yourself/>
> - Ignorância de persistência  
> <http://deviq.com/persistence-ignorance/>
> - **Contexto limitado**  
> <https://martinfowler.com/bliki/BoundedContext.html>

> [!div class="step-by-step"]
[Anterior] (choose-between-traditional-web-and-single-page-apps.md) [Avançar] (comum-web-aplicativo-architectures.md)
