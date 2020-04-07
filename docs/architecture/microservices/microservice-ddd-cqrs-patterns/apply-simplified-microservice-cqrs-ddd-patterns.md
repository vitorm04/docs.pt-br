---
title: Aplicando padrões CQRS e DDD simplificados em um microsserviço
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Entender a relação geral entre os padrões CQRS e DDD.
ms.date: 10/08/2018
ms.openlocfilehash: e4e36bafff39f5f30d6371ed7c113322a85c3362
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805583"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Aplicar padrões CQRS e DDD simplificados em um microsserviço

O CQRS é um padrão de arquitetura que separa os modelos para ler e gravar dados. O termo relacionado [CQS (Separação de Comando-Consulta)](https://martinfowler.com/bliki/CommandQuerySeparation.html) foi originalmente definido por Bertrand Meyer em seu livro *Object Oriented Software Construction* (Construção de software orientada a objeto). A idéia básica é que você pode dividir as operações de um sistema em duas categorias bem separadas:

- Consultas. Essas retornam um resultado, não alteram o estado do sistema e são livres de efeitos colaterais.

- comandos. Esses alteram o estado de um sistema.

CQS é um conceito simples: trata-se de métodos dentro do mesmo objeto sendo consultas ou comandos. Cada método retorna um estado ou muda um estado, mas não ambos. Até mesmo um único objeto de padrão de repositório pode estar em conformidade com o CQS. O CQS pode ser considerado um princípio fundamental para o CQRS.

O [CQRS (Segregação de Responsabilidade de Consulta e Comando)](https://martinfowler.com/bliki/CQRS.html) foi introduzido por Greg Young e altamente promovido por Udi Dahan e outros. Ele se baseia no princípio do CQS, embora seja mais detalhado. Ele pode ser considerado um padrão com base em comandos e eventos, além de ser opcional em mensagens assíncronas. Em muitos casos, o CQRS está relacionado a cenários mais avançados, como ter um banco de dados físico para leituras (consultas) diferente do banco de dados para gravações (atualizações). Além disso, um sistema CQRS mais evoluído pode implementar [ES (fonte de eventos)](https://martinfowler.com/eaaDev/EventSourcing.html) em seu banco de dados de atualizações. Assim, você deve apenas armazenar eventos no modelo de domínio, em vez de armazenar os dados do estado atual. No entanto, esta abordagem não é usada neste guia. Este guia usa a abordagem CQRS mais simples, que consiste apenas em separar as consultas dos comandos.

O aspecto de separação do CQRS é obtido pelo agrupamento de operações de consulta em uma camada e comandos em outra camada. Cada camada tem seu próprio modelo de dados (observe que dizemos modelo, não necessariamente um banco de dados diferente) e é criada usando sua própria combinação de padrões e tecnologias. Além disso, as duas camadas podem estar dentro do mesmo nível ou microsserviço, como no exemplo (microsserviço de ordenação) usado para este guia. Ou elas podem ser implementadas em diferentes microsserviços ou processos para que possam ser otimizadas e expandidas separadamente sem afetar umas às outras.

CQRS significa ter dois objetos para uma operação de leitura/gravação, em que, em outros, há um. Há motivos para ter um banco de dados de leitura desnormalizado, sobre o qual você pode aprender na literatura sobre CQRS mais avançada. Mas não estamos usando essa abordagem aqui, em que a meta é ter mais flexibilidade nas consultas, em vez de limitá-las com restrições de padrões DDD como agregações.

Um exemplo desse tipo de serviço é o microsserviço de ordenação do aplicativo eShopOnContainers de referência. Este serviço implementa um microsserviço com base em uma abordagem CQRS simplificada. Ele usa uma única fonte de dados ou banco de dados, mas dois modelos lógicos, além de padrões DDD para o domínio transacional, conforme mostrado na Figura 7-2.

![Diagrama mostrando um microserviço CQRS e DDD simplificado de alto nível.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Figura 7-2**. Microsserviço baseado em CQRS e DDD simplificado

O Microservice lógico "Ordering" inclui seu banco de dados de pedidos, que pode ser, mas não precisa ser, o mesmo host Docker. É bom ter o banco de dados no mesmo host do Docker para desenvolvimento, mas não para produção.

A camada de aplicativo pode ser a própria API Web. O aspecto de design importante aqui é que o microsserviço dividiu as consultas e ViewModels (modelos de dados criados especialmente para os aplicativos cliente) dos comandos, do modelo de domínio e das transações que seguem o padrão CQRS. Essa abordagem mantém as consultas independentes de restrições provenientes de padrões DDD que só fazem sentido para transações e atualizações, conforme explicado nas seções posteriores.

## <a name="additional-resources"></a>Recursos adicionais

- **O Greg Young. Versão em um sistema de origem de eventos** (livre para ler e-book on-line) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](eshoponcontainers-cqrs-ddd-microservice.md)
