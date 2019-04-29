---
title: Aplicativos lógicos do Azure - aplicativos sem servidor
description: Aplicativos lógicos do Azure permitir a construção dimensionáveis fluxos de trabalho automatizados que integram aplicativos e sistemas locais e serviços de dados na nuvem.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 14670a8459db3b80b8fbe3139c2675321cf9592c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712745"
---
# <a name="azure-logic-apps"></a>Aplicativos Lógicos do Azure

[Aplicativos lógicos do Azure](https://docs.microsoft.com/azure/logic-apps) fornece um mecanismo sem servidor para criar fluxos de trabalho automatizados para integrar aplicativos e dados entre os serviços de nuvem e sistemas locais. Você cria fluxos de trabalho usando um designer visual. Você pode disparar fluxos de trabalho com base em eventos, temporizadores e aproveite conectores para aplicativos de integração e facilitar a comunicação de business-to-business (B2B). Os aplicativos lógicos se integra perfeitamente com o Azure Functions.

![Logotipo de aplicativos lógicos do Azure](./media/logic-apps-logo.png)

Os aplicativos lógicos podem fazer mais do que simplesmente se conectar aos serviços de nuvem (como funções) com recursos de nuvem (como filas e os bancos de dados). Você também pode organizar os fluxos de trabalho local com o gateway local. Por exemplo, você pode usar o aplicativo lógico para disparar a lógica condicional no fluxo de trabalho ou um procedimento armazenado SQL local, em resposta a um evento baseado em nuvem. Saiba mais sobre [conectando-se a fontes de dados locais com o Gateway de dados local do Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Arquitetura de aplicativos lógicos](./media/logic-apps-architecture.png)

Como o Azure Functions, disparar fluxos de trabalho de aplicativo lógico com um gatilho. Há vários gatilhos para sua escolha. A captura a seguir mostra algumas das mais populares aqueles fora de centenas que estão disponíveis.

![Gatilhos de aplicativos lógicos](./media/logic-app-triggers.png)

Depois que o aplicativo é disparado, você pode usar o designer visual para criar etapas, loops, condições e ações. Todos os dados ingeridos em uma etapa anterior estão disponíveis para uso nas próximas etapas. O fluxo de trabalho a seguir carrega URLs de um banco de dados do CosmosDB. Ele localiza aqueles com um host de `t.co` , em seguida, procura-los no Twitter. Se ele encontrar tweets correspondentes, ele atualiza os documentos com os tweets relacionados ao chamar uma função.

![Fluxo de trabalho de aplicativo lógico](./media/logic-app-workflow.png)

O painel de aplicativos lógicos mostra o histórico da execução de seus fluxos de trabalho e se cada execução foi concluída com êxito ou não. Você pode navegar em qualquer execução e inspecione os dados usados por cada etapa para solução de problemas. Os aplicativos lógicos também fornecem modelos existentes, você pode editar e é bem adequados para fluxos de trabalho empresariais complexos.

Para obter mais informações, consulte [aplicativos lógicos do Azure](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Anterior](application-insights.md)
>[Próximo](event-grid.md)