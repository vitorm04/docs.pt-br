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
# <a name="azure-logic-apps"></a><span data-ttu-id="78131-103">Aplicativos Lógicos do Azure</span><span class="sxs-lookup"><span data-stu-id="78131-103">Azure Logic Apps</span></span>

<span data-ttu-id="78131-104">[O Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) fornece um mecanismo sem servidor para criar fluxos de trabalho automatizados para integrar aplicativos e dados entre serviços de nuvem e sistemas locais.</span><span class="sxs-lookup"><span data-stu-id="78131-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="78131-105">Você constrói fluxos de trabalho usando um designer visual.</span><span class="sxs-lookup"><span data-stu-id="78131-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="78131-106">Você pode acionar fluxos de trabalho com base em eventos ou temporizadores e aproveitar conectores para aplicativos de integração e facilitar a comunicação business-to-business (B2B).</span><span class="sxs-lookup"><span data-stu-id="78131-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="78131-107">Logic Apps integra-se perfeitamente com funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="78131-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logotipo da Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="78131-109">Logic Apps podem fazer mais do que apenas conectar seus serviços em nuvem (como funções) com recursos na nuvem (como filas e bancos de dados).</span><span class="sxs-lookup"><span data-stu-id="78131-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="78131-110">Você também pode orquestrar fluxos de trabalho no local com o gateway no local.</span><span class="sxs-lookup"><span data-stu-id="78131-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="78131-111">Por exemplo, você pode usar o Logic App para ativar um procedimento armazenado no local sql em resposta a um evento baseado em nuvem ou lógica condicional em seu fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="78131-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="78131-112">Saiba mais sobre [a conexão com fontes de dados locais com o Gateway de dados on-premises do Azure .](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)</span><span class="sxs-lookup"><span data-stu-id="78131-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Arquitetura de aplicativos lógicos](./media/logic-apps-architecture.png)

<span data-ttu-id="78131-114">Como funções do Azure, você inicia fluxos de trabalho do Logic App com um gatilho.</span><span class="sxs-lookup"><span data-stu-id="78131-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="78131-115">Há muitos gatilhos para você escolher.</span><span class="sxs-lookup"><span data-stu-id="78131-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="78131-116">A captura a seguir mostra apenas alguns dos mais populares entre centenas que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="78131-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Gatilhos de Aplicativos Lógicos](./media/logic-app-triggers.png)

<span data-ttu-id="78131-118">Uma vez que o aplicativo é acionado, você pode usar o designer visual para construir etapas, loops, condições e ações.</span><span class="sxs-lookup"><span data-stu-id="78131-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="78131-119">Todos os dados ingeridos em uma etapa anterior estão disponíveis para você usar em etapas subseqüentes.</span><span class="sxs-lookup"><span data-stu-id="78131-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="78131-120">O fluxo de trabalho a seguir carrega URLs de um banco de dados CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="78131-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="78131-121">Ele encontra aqueles com `t.co` uma série de então procura por eles no Twitter.</span><span class="sxs-lookup"><span data-stu-id="78131-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="78131-122">Se encontrar tweets correspondentes, ele atualizará os documentos com os tweets relacionados chamando uma função.</span><span class="sxs-lookup"><span data-stu-id="78131-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Fluxo de trabalho do App lógico](./media/logic-app-workflow.png)

<span data-ttu-id="78131-124">O painel de aplicativos lógicos mostra o histórico de execução de seus fluxos de trabalho e se cada execução foi concluída com sucesso ou não.</span><span class="sxs-lookup"><span data-stu-id="78131-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="78131-125">Você pode navegar em qualquer execução dada e inspecionar os dados usados por cada etapa para solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="78131-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="78131-126">Logic Apps também fornece modelos existentes que você pode editar e são adequados para fluxos de trabalho corporativos complexos.</span><span class="sxs-lookup"><span data-stu-id="78131-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="78131-127">Para saber mais, consulte [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="78131-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="78131-128">[Próximo](application-insights.md)
>[anterior](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="78131-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
