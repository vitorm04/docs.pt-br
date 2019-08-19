---
title: Aplicativos lógicos do Azure-aplicativos sem servidor
description: Os aplicativos lógicos do Azure permitem a criação de fluxos de trabalho escalonáveis automatizados que integram aplicativos e dados entre serviços de nuvem e sistemas locais.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577449"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="579a0-103">Aplicativos Lógicos do Azure</span><span class="sxs-lookup"><span data-stu-id="579a0-103">Azure Logic Apps</span></span>

<span data-ttu-id="579a0-104">O [aplicativo lógico do Azure](https://docs.microsoft.com/azure/logic-apps) fornece um mecanismo sem servidor para criar fluxos de trabalho automatizados para integrar aplicativos e dados entre serviços de nuvem e sistemas locais.</span><span class="sxs-lookup"><span data-stu-id="579a0-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="579a0-105">Você cria fluxos de trabalho usando um designer visual.</span><span class="sxs-lookup"><span data-stu-id="579a0-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="579a0-106">Você pode disparar fluxos de trabalho com base em eventos ou temporizadores e aproveitar os conectores para aplicativos de integração e facilitar a comunicação entre empresas (B2B).</span><span class="sxs-lookup"><span data-stu-id="579a0-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="579a0-107">Os aplicativos lógicos se integram perfeitamente com Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="579a0-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logotipo do aplicativo lógico do Azure](./media/logic-apps-logo.png)

<span data-ttu-id="579a0-109">Os aplicativos lógicos podem fazer mais do que apenas conectar seus serviços de nuvem (como funções) com recursos de nuvem (como filas e bancos de dados).</span><span class="sxs-lookup"><span data-stu-id="579a0-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="579a0-110">Você também pode orquestrar fluxos de trabalho locais com o gateway local.</span><span class="sxs-lookup"><span data-stu-id="579a0-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="579a0-111">Por exemplo, você pode usar o aplicativo lógico para disparar um procedimento armazenado SQL local em resposta a um evento baseado em nuvem ou lógica condicional em seu fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="579a0-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="579a0-112">Saiba mais sobre como [se conectar a fontes de dados locais com o gateway de dados local do Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="579a0-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Arquitetura de aplicativos lógicos](./media/logic-apps-architecture.png)

<span data-ttu-id="579a0-114">Assim como Azure Functions, você inicia fluxos de trabalho de aplicativo lógico com um gatilho.</span><span class="sxs-lookup"><span data-stu-id="579a0-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="579a0-115">Há muitos disparadores para sua escolha.</span><span class="sxs-lookup"><span data-stu-id="579a0-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="579a0-116">A captura a seguir mostra apenas alguns dos mais populares de centenas que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="579a0-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Gatilhos de aplicativos lógicos](./media/logic-app-triggers.png)

<span data-ttu-id="579a0-118">Depois que o aplicativo é disparado, você pode usar o designer visual para criar etapas, loops, condições e ações.</span><span class="sxs-lookup"><span data-stu-id="579a0-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="579a0-119">Todos os dados ingeridos em uma etapa anterior estão disponíveis para uso nas etapas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="579a0-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="579a0-120">O fluxo de trabalho a seguir carrega URLs de um banco de dados CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="579a0-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="579a0-121">Ele localiza aqueles com um host de `t.co` e, em seguida, pesquisa-os no Twitter.</span><span class="sxs-lookup"><span data-stu-id="579a0-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="579a0-122">Se encontrar tweets correspondentes, ele atualizará os documentos com os tweets relacionados chamando uma função.</span><span class="sxs-lookup"><span data-stu-id="579a0-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Fluxo de trabalho do aplicativo lógico](./media/logic-app-workflow.png)

<span data-ttu-id="579a0-124">O painel aplicativos lógicos mostra o histórico da execução de seus fluxos de trabalho e se cada execução foi concluída com êxito ou não.</span><span class="sxs-lookup"><span data-stu-id="579a0-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="579a0-125">Você pode navegar para qualquer execução específica e inspecionar os dados usados por cada etapa para solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="579a0-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="579a0-126">Os aplicativos lógicos também fornecem modelos existentes que você pode editar e são adequados para fluxos de trabalho empresariais complexos.</span><span class="sxs-lookup"><span data-stu-id="579a0-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="579a0-127">Para saber mais, consulte [aplicativos lógicos do Azure](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="579a0-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="579a0-128">[Anterior](application-insights.md)
>[Próximo](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="579a0-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
