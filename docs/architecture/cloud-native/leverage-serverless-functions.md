---
title: Como aproveitar funções sem servidor
description: Aproveitamento e Azure Functions sem servidor em aplicativos nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: c79f611b83f63079634fb2bac037c99f851f18ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578921"
---
# <a name="leveraging-serverless-functions"></a>Como aproveitar funções sem servidor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

No espectro de gerenciamento de computadores e sistemas operacionais completos para aproveitar os recursos de nuvem, as vidas sem servidor no fim extremo em que a única coisa que você é responsável é seu código, e você só paga quando seu código é executado. Azure Functions fornece uma maneira de criar recursos sem servidor em seus aplicativos. 

## <a name="what-is-serverless"></a>O que é sem servidor?

A computação sem servidor não significa que não haja um servidor envolvido na execução do aplicativo-o código ainda é executado em um servidor em algum lugar. A diferença é que a equipe de desenvolvimento de aplicativos não precisa mais se preocupar com o gerenciamento da infraestrutura do servidor. Soluções de computação sem servidor como Azure Functions ajudam as equipes a aumentarem a produtividade e permitir que as organizações otimizem seus recursos e se concentrem em fornecer soluções.

A computação sem servidor usa contêineres com estado disparado por eventos para hospedar seu aplicativo ou parte do seu aplicativo. As plataformas sem servidor podem escalar horizontalmente e em para atender à demanda conforme necessário. Plataformas como Azure Functions têm acesso fácil direto a outros serviços do Azure, como filas, eventos e armazenamento.

## <a name="what-challenges-are-solved-by-serverless"></a>Quais desafios são resolvidos sem servidor?

Sem servidor é a abstração final para longe da execução de seu próprio hardware. Os desenvolvedores podem se concentrar exclusivamente em escrever código para resolver problemas de negócios, sem preocupação com qualquer uma das seguintes tarefas que possam ter sido necessárias ao hospedar seus próprios servidores:

- Compra de computadores e licenças de software
- Hospedagem, proteção, configuração e manutenção de computadores e seus requisitos de rede, energia e/C
- Aplicação de patch e atualização de software e sistemas operacionais
- Configurando servidores Web ou serviços de máquina para hospedar software de aplicativo
- Configurando o software de aplicativo em sua plataforma

Muitas empresas empregam dezenas de membros da equipe e alocam grandes orçamentos para dar suporte a essas questões de infraestrutura de hardware. Simplesmente mudar para a nuvem elimina algumas dessas preocupações; a mudança de aplicativos para o servidor eliminará o restante.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Quais cenários são apropriados para servidores sem servidor?

Sem servidor usa funções de curta execução individuais que são chamadas em resposta a algum gatilho. Isso os torna ideais para o processamento de tarefas em segundo plano.

Por exemplo, um aplicativo pode precisar enviar um email como parte do processamento de uma solicitação. Em vez de enviar o email como parte do tratamento da solicitação da Web, os detalhes do email podem ser colocados em uma fila e uma função do Azure pode ser usada para pegar a mensagem e enviar o email. Muitas partes diferentes do aplicativo, ou até mesmo muitos aplicativos, podem aproveitar esse mesmo Azure Function, fornecendo melhor desempenho e escalabilidade para os aplicativos e usando o [nivelamento de carga baseado em fila](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) para evitar gargalos relacionados a enviando os emails.

Embora um [padrão de editor/assinante](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) entre aplicativos e Azure Functions seja o padrão mais comum, outros padrões são possíveis. Azure Functions pode ser disparado por outros eventos, como alterações no armazenamento de BLOBs do Azure. Um aplicativo com suporte para carregamentos de imagem pode ter uma função do Azure responsável por criar imagens em miniatura ou redimensionar imagens carregadas para dimensões consistentes ou otimizar o tamanho da imagem. Toda essa funcionalidade poderia ser disparada diretamente por inserções no armazenamento de BLOBs do Azure, mantendo a complexidade e a carga de trabalho fora do próprio aplicativo.

Muitos aplicativos têm processos de execução longa como parte de seus fluxos de trabalho. Muitas vezes, essas tarefas são feitas como parte da interação do usuário com o aplicativo, forçando o usuário a aguardar e afetar negativamente sua experiência. A computação sem servidor fornece uma ótima maneira de executar tarefas mais lentas fora do loop de interação do usuário, e essas tarefas podem ser facilmente dimensionadas com demanda sem exigir que todo o aplicativo seja dimensionado.

## <a name="when-should-you-avoid-serverless"></a>Quando você não deve evitar servidor?

A computação sem servidor é melhor usada para tarefas que não bloqueiam a interface do usuário. Isso significa que eles não são ideais para hospedar aplicativos Web ou APIs Web diretamente. O principal motivo para isso é que as soluções sem servidor são provisionadas e dimensionadas sob demanda. Quando uma nova instância de uma função é necessária, chamada de inicialização a *frio*, leva tempo para provisionar. Esse tempo é normalmente de alguns segundos, mas pode ser mais demorado dependendo de uma variedade de fatores. Uma única instância pode, muitas vezes, ser mantida ativa indefinidamente (por exemplo, fazendo uma solicitação periodicamente), mas o problema de inicialização a frio permanece se o número de instâncias precisar ser escalado verticalmente.

![Cold versus inicialização a quente ](./media/cold-start-warm-start.png)
**figura 3-10**. Início frio versus início quente.

Se você precisar evitar a inicialização a frio, poderá optar por alternar de um [plano de consumo para um plano dedicado](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Você também pode [Configurar uma ou mais instâncias pré-configuradas](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) com o plano Premium para que, quando precisar adicionar outra instância, já esteja pronto e pronta para começar. Essas opções podem atenuar uma das principais preocupações associadas à computação sem servidor.

Normalmente, você também deve evitar servidores sem servidor para tarefas de longa execução. Elas são melhores para pequenas partes de trabalho que podem ser concluídas rapidamente. A maioria das plataformas sem servidor exige que as funções individuais sejam concluídas em alguns minutos. Azure Functions usa como padrão uma duração de tempo limite de 5 minutos (pode ser configurada até 10 minutos). O plano Azure Functions Premium também pode mitigar esse problema, padronizando o tempo limite para 30 minutos e permitindo que um limite mais alto não associado seja configurado.

Por fim, o uso sem servidor para determinadas tarefas em seu aplicativo adiciona complexidade. Geralmente, é melhor arquitetar seu aplicativo de maneira modular e rigidamente acoplada primeiro e, em seguida, identificar se há benefícios que o servidor não oferece a maior complexidade que vale a pena. Muitos aplicativos menores serão executados perfeitamente bem em uma única implantação monolítica, sem a necessidade de que a computação sem servidor da arquitetura de aplicativo distribuído exija.

## <a name="references"></a>Referências

- [Entendendo a inicialização a frio sem servidor](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Instâncias de Azure Functions previamente passivas](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Criar uma função no Linux usando uma imagem personalizada](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
>[Anterior](leverage-containers-orchestrators.md)
>[Próximo](combine-containers-serverless-approaches.md)
