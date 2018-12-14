---
title: Aplicando padrões CQRS e DDD simplificados em um microsserviço
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Entender a relação geral entre os padrões CQRS e DDD.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ef3260143c91c2500becd7c8c1a6cd0b81dbf3d2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148061"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Aplicar padrões CQRS e DDD simplificados em um microsserviço

O CQRS é um padrão de arquitetura que separa os modelos para ler e gravar dados. O termo relacionado [CQS (Separação de Comando-Consulta)](https://martinfowler.com/bliki/CommandQuerySeparation.html) foi originalmente definido por Bertrand Meyer em seu livro *Object Oriented Software Construction* (Construção de software orientada a objeto). A ideia básica é que você pode dividir operações de um sistema em duas categorias nitidamente separadas:

- Consultas. Essas retornam um resultado, não alteram o estado do sistema e são livres de efeitos colaterais.

- Comandos. Esses alteram o estado de um sistema.

O CQS é um conceito simples — trata-se de métodos dentro do mesmo objeto sendo consultas ou comandos. Cada método retorna um estado ou muda um estado, mas não ambos. Até mesmo um único objeto de padrão de repositório pode estar em conformidade com o CQS. O CQS pode ser considerado um princípio fundamental para o CQRS.

O [CQRS (Segregação de Responsabilidade de Consulta e Comando)](https://martinfowler.com/bliki/CQRS.html) foi introduzido por Greg Young e altamente promovido por Udi Dahan e outros. Ele se baseia no princípio do CQS, embora seja mais detalhado. Ele pode ser considerado um padrão com base em comandos e eventos, além de ser opcional em mensagens assíncronas. Em muitos casos, o CQRS está relacionado a cenários mais avançados, como ter um banco de dados físico para leituras (consultas) diferente do banco de dados para gravações (atualizações). Além disso, um sistema CQRS mais evoluído pode implementar [ES (fonte de eventos)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) em seu banco de dados de atualizações. Assim, você deve apenas armazenar eventos no modelo de domínio, em vez de armazenar os dados do estado atual. No entanto, essa não é a abordagem usada neste guia; estamos usando a abordagem mais simples de CQRS, que consiste em separar apenas as consultas dos comandos.

O aspecto de separação do CQRS é obtido pelo agrupamento de operações de consulta em uma camada e comandos em outra camada. Cada camada tem seu próprio modelo de dados (observe que dizemos modelo, não necessariamente um banco de dados diferente) e é criada usando sua própria combinação de padrões e tecnologias. Além disso, as duas camadas podem estar dentro do mesmo nível ou microsserviço, como no exemplo (microsserviço de ordenação) usado para este guia. Ou elas podem ser implementadas em diferentes microsserviços ou processos para que possam ser otimizadas e expandidas separadamente sem afetar umas às outras.

CQRS significa ter dois objetos para uma operação de leitura/gravação, em que, em outros, há um. Há motivos para ter um banco de dados de leitura desnormalizado, sobre o qual você pode aprender na literatura sobre CQRS mais avançada. Mas não estamos usando essa abordagem aqui, em que a meta é ter mais flexibilidade nas consultas, em vez de limitá-las com restrições de padrões DDD como agregações.

Um exemplo desse tipo de serviço é o microsserviço de ordenação do aplicativo eShopOnContainers de referência. Este serviço implementa um microsserviço com base em uma abordagem CQRS simplificada. Ele usa uma única fonte de dados ou banco de dados, mas dois modelos lógicos, além de padrões DDD para o domínio transacional, conforme mostrado na Figura 7-2.

![O microsserviço Pedidos lógico inclui o banco de dados do Pedidos, que pode estar ou não no mesmo host do Docker. É bom ter o banco de dados no mesmo host do Docker para desenvolvimento, mas não para produção.](./media/image2.png)

**Figura 7-2**. Microsserviço baseado em CQRS e DDD simplificado

A camada de aplicativo pode ser a própria API Web. O aspecto de design importante aqui é que o microsserviço dividiu as consultas e ViewModels (modelos de dados criados especialmente para os aplicativos cliente) dos comandos, do modelo de domínio e das transações que seguem o padrão CQRS. Essa abordagem mantém as consultas independentes de restrições provenientes de padrões DDD que só fazem sentido para transações e atualizações, conforme explicado nas seções posteriores.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](eshoponcontainers-cqrs-ddd-microservice.md)