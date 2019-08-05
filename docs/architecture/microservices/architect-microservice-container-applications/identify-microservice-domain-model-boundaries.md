---
title: Identificando os limites de modelo de domínio de cada microsserviço
description: Explore a essência do particionamento de um aplicativo grande em microsserviços para alcançar uma arquitetura sólida.
ms.date: 09/20/2018
ms.openlocfilehash: aa903e13b20be1084fad60e6fb7bbb1c61403deb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673083"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identificar os limites de modelo de domínio de cada microsserviço

A meta de identificar os limites do modelo e o tamanho de cada microsserviço não é obter a separação mais granular possível, embora você deva tender a usar microsserviços pequenos se possível. Em vez disso, sua meta deve ser obter a separação mais significativa orientada pelo seu conhecimento do domínio. A ênfase não está no tamanho, mas em funcionalidades empresariais. Além disso, se for necessária uma clara coesão para uma determinada área do aplicativo com base em um grande número de dependências, isso será a indicação da necessidade de um único microsserviço também. A coesão é uma maneira de identificar como separar ou agrupar microsserviços. Por fim, enquanto você obtém mais conhecimento sobre o domínio, deve adaptar o tamanho do seu microsserviço iterativamente. Localizar o tamanho correto não é um processo único.

[SAM Newman](https://samnewman.io/), um conhecido promotor de microsserviços e autor do livro [Building microservices](https://samnewman.io/books/building_microservices/) (Criando microsserviços), realça o que você deve projetar seus microsserviços com base no padrão de BC (Contexto Limitado) (parte do controlado por domínio design), conforme apresentado anteriormente. Às vezes, um BC poderia ser composto por vários serviços físicos, mas não vice-versa.

Um modelo de domínio com entidades de domínio específicas dentro de um BC ou microsserviço concreto. Um BC delimita a aplicabilidade de um modelo de domínio e dá aos membros da equipe do desenvolvedor uma compreensão clara e compartilhada sobre o que deve ser coeso e o que pode ser desenvolvido de modo independente. Essas são as mesmas metas de microsserviços.

Outra ferramenta que informa a sua escolha de design é a [lei de Conway](https://en.wikipedia.org/wiki/Conway%27s_law), que diz que um aplicativo refletirá os limites sociais da organização que o produziu. Porém, às vezes, o oposto é verdadeiro: a organização da empresa é formada pelo software. Talvez você precise reverter a lei de Conway e criar os limites de compilação da maneira que deseja que a empresa seja organizada, inclinada em direção à consultoria do processo empresarial.

Para identificar contextos limitados, você pode usar um padrão DDD chamado de [padrão de mapeamento de contexto](https://www.infoq.com/articles/ddd-contextmapping). Com Mapeamento de Contexto, você identifica os vários contextos no aplicativo e seus limites. É comum haver um contexto e um limite diferentes para cada subsistema pequeno, por exemplo. O Mapa de Contexto é uma maneira de definir e explicitar esses limites entre domínios. Um BC é autônomo e inclui os detalhes de um único domínio (detalhes como as entidades de domínio) e define os contratos de integração com outros BCs. Isso é semelhante à definição de um microsserviço: é autônomo, implementa determinadas funcionalidades de domínio e deve fornecer interfaces. É por isso que o Mapeamento de Contexto e o padrão de Contexto Limitado são boas abordagens para identificar os limites de modelo de domínio dos seus microsserviços.

Ao criar um aplicativo grande, você verá como seu modelo de domínio pode ser fragmentado; um especialista de domínio do domínio de catálogo nomeará as entidades de maneira diferente nos domínios de catálogo e de inventário que um especialista em domínio de envio, por exemplo. Ou a entidade de usuário de domínio pode ser diferente em termos de tamanho e número de atributos ao lidar com um especialista do CRM que queira armazenar todos os detalhes sobre o cliente do que ao lidar com um especialista de domínio de ordenação que precisa apenas de dados parciais sobre o cliente. É muito difícil resolver a ambiguidade de todos os termos do domínio em todos os domínios relacionados a um aplicativo grande. Mas o mais importante é que você não deve tentar unificar os termos. Em vez disso, aceite as diferenças e riqueza fornecida pelos domínios individuais. Se você tentar obter um banco de dados unificado para o aplicativo inteiro, tentativas de um vocabulário unificada serão inadequadas e não soarão bem a nenhum dos vários especialistas de domínio. Portanto, BCs (implementados como microsserviços) ajudarão a esclarecer em que locais você pode usar determinados termos do domínio e em que locais precisará dividir o sistema e criar BCs adicionais com domínios diferentes.

Você saberá que obteve os limites e tamanhos certos de cada BC e modelo de domínio se tiver alguma relação forte entre modelos de domínio e normalmente não precisará mesclar informações de vários modelos de domínio ao executar um operações de aplicativo típicas.

Talvez a melhor resposta à pergunta de quão grande um modelo de domínio para cada microsserviço deve ser é a seguinte: ele deve ter um BC autônomo, o mais isolado possível, que lhe permita trabalhar sem precisar mudar constantemente para outros contextos (outros modelos do microsserviço). Na Figura 4-10, você pode ver como cada um dos vários microsserviços (vários BCs) tem seus próprios modelos e como suas entidades podem ser definidas, dependendo dos requisitos específicos para cada um dos domínios identificados em seu aplicativo.

![Modelo de entidades em vários limites (contextos limitados), em que a mesma entidade aparece como "Usuários", "Compradores", "Clientes médica" e "Clientes", dependendo do contexto limitado](./media/image10.png)

**Figura 4-10**. Identificação de entidades e limites de modelo de microsserviço

A Figura 4-10 ilustra um cenário de exemplo relacionado a um sistema de gerenciamento de conferência online. Você identificou vários BCs que podem ser implementados como microsserviços, com base em domínios que especialistas de domínio definiram para você. Como você pode ver, há entidades que estão presentes apenas em um único modelo de microsserviço, como Pagamentos no microsserviço de Pagamento. Esses serão fáceis de implementar.

No entanto, você também pode ter entidades com diferentes formas, mas que compartilhem de uma mesma identidade em vários modelos de domínio de vários microsserviços. Por exemplo, a entidade de Usuário é identificada no microsserviço Gerenciamento de Conferências. Esse mesmo usuário, com a mesma identidade, é o chamado Compradores no microsserviço de Ordenação ou o chamado Pagante no microsserviço de Pagamento e, até mesmo, o chamado Cliente no microsserviço de Atendimento ao Cliente. Isso ocorre porque, dependendo da [linguagem ubíqua](https://martinfowler.com/bliki/UbiquitousLanguage.html) que cada especialista em domínio está usando, um usuário pode ter uma perspectiva diferente mesmo com atributos diferentes. A entidade de usuário no modelo de microsserviço denominado Gerenciamento de Conferências pode ter a maioria dos seus atributos de dados pessoais. No entanto, esse mesmo usuário na forma Pagante no microsserviço Pagamento ou na forma de Cliente no microsserviço Atendimento ao Cliente talvez não precise da mesma lista de atributos.

Uma abordagem similar é ilustrada na Figura 4-11.

![Ao decompor um modelo de dados tradicional entre contextos limitados, você pode ter entidades diferentes que compartilham a mesma identidade (um comprador também é um usuário) com atributos diferentes em cada contexto limitado.](./media/image11.png)

**Figura 4-11**. Decomposição de modelos de dados tradicionais em vários modelos de domínio

Você pode ver como o usuário está presente no modelo de microsserviço de Gerenciamento de Conferências como a entidade de Usuário e também está presente na forma de entidade de Comprador no microsserviço Preços, com atributos ou detalhes alternativos sobre o usuário quando ele é de fato um Comprador. Cada microsserviço ou BC pode não precisar de todos os dados relacionados a uma entidade de Usuário, apenas parte deles, dependendo do problema ou do contexto a resolver. Por exemplo, no modelo de microsserviço de Preços, não é necessário o endereço nem o nome do usuário, apenas a ID (como identidade) e o Status, que afetarão os descontos ao definir os preços das estações por comprador.

A entidade Seat tem o mesmo nome, mas diferentes atributos em cada modelo de domínio. No entanto, Seat compartilha identidade com base na mesma ID, conforme acontece com Usuário e Comprador.

Basicamente, há um conceito compartilhado de um usuário que existe em vários serviços (domínios), que compartilham todos da identidade do usuário. Mas, em cada modelo de domínio, pode haver detalhes adicionais ou diferentes sobre a entidade de usuário. Portanto, precisa haver uma maneira de mapear uma entidade de usuário de um domínio (microsserviço) para outro.

Existem vários benefícios em não compartilhar a mesma entidade de usuário com o mesmo número de atributos entre domínios. Um benefício é reduzir a duplicação para que os modelos de microsserviço não tenham nenhum dado de que não precisem. Outro benefício é ter um microsserviço mestre que detém um determinado tipo de dados por entidade de modo que atualizações e consultas para esse tipo de dados sejam controladas apenas por esse microsserviço.

>[!div class="step-by-step"]
>[Anterior](distributed-data-management.md)
>[Próximo](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
