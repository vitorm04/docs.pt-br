---
title: Azure Logic Apps - Aplicativos sem servidor
description: Os Aplicativos de Lógica do Azure permitem criar fluxos de trabalho escaláveis automatizados que integram aplicativos e dados em serviços de nuvem e sistemas locais.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577449"
---
# <a name="azure-logic-apps"></a>Aplicativos Lógicos do Azure

[O Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) fornece um mecanismo sem servidor para criar fluxos de trabalho automatizados para integrar aplicativos e dados entre serviços de nuvem e sistemas locais. Você constrói fluxos de trabalho usando um designer visual. Você pode acionar fluxos de trabalho com base em eventos ou temporizadores e aproveitar conectores para aplicativos de integração e facilitar a comunicação business-to-business (B2B). Logic Apps integra-se perfeitamente com funções do Azure.

![Logotipo da Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps podem fazer mais do que apenas conectar seus serviços em nuvem (como funções) com recursos na nuvem (como filas e bancos de dados). Você também pode orquestrar fluxos de trabalho no local com o gateway no local. Por exemplo, você pode usar o Logic App para ativar um procedimento armazenado no local sql em resposta a um evento baseado em nuvem ou lógica condicional em seu fluxo de trabalho. Saiba mais sobre [a conexão com fontes de dados locais com o Gateway de dados on-premises do Azure .](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)

![Arquitetura de aplicativos lógicos](./media/logic-apps-architecture.png)

Como funções do Azure, você inicia fluxos de trabalho do Logic App com um gatilho. Há muitos gatilhos para você escolher. A captura a seguir mostra apenas alguns dos mais populares entre centenas que estão disponíveis.

![Gatilhos de Aplicativos Lógicos](./media/logic-app-triggers.png)

Uma vez que o aplicativo é acionado, você pode usar o designer visual para construir etapas, loops, condições e ações. Todos os dados ingeridos em uma etapa anterior estão disponíveis para você usar em etapas subseqüentes. O fluxo de trabalho a seguir carrega URLs de um banco de dados CosmosDB. Ele encontra aqueles com `t.co` uma série de então procura por eles no Twitter. Se encontrar tweets correspondentes, ele atualizará os documentos com os tweets relacionados chamando uma função.

![Fluxo de trabalho do App lógico](./media/logic-app-workflow.png)

O painel de aplicativos lógicos mostra o histórico de execução de seus fluxos de trabalho e se cada execução foi concluída com sucesso ou não. Você pode navegar em qualquer execução dada e inspecionar os dados usados por cada etapa para solução de problemas. Logic Apps também fornece modelos existentes que você pode editar e são adequados para fluxos de trabalho corporativos complexos.

Para saber mais, consulte [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Próximo](application-insights.md)
>[anterior](event-grid.md)
