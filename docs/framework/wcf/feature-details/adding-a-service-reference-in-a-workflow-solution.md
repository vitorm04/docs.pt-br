---
title: "Adicionando uma referência de serviço em uma solução de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="e8e91-102">Adicionando uma referência de serviço em uma solução de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e8e91-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="e8e91-103">Adicionar uma referência de serviço em um aplicativo de fluxo de trabalho funciona um pouco diferente de um aplicativo WCF regular.</span><span class="sxs-lookup"><span data-stu-id="e8e91-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="e8e91-104">Quando você seleciona Adicionar referência de serviço e especifique a URL para o serviço de metadados é baixado e atividades personalizadas são geradas que permitem que você chamar o serviço WCF ou serviço de fluxo de trabalho WCF que você adicionou uma referência para.</span><span class="sxs-lookup"><span data-stu-id="e8e91-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="e8e91-105">Depois de adicionar uma referência de serviço, recompile a solução para que as atividades geradas são criadas.</span><span class="sxs-lookup"><span data-stu-id="e8e91-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="e8e91-106">Em seguida, eles serão exibidos na caixa de ferramentas de designer da fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e8e91-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="e8e91-107">No entanto, observe que isso só funcionará se você estiver adicionando uma referência de serviço dentro de uma solução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e8e91-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="e8e91-108">A conversão de web a seguir mostra como adicionar uma referência de serviço em outros tipos de projetos: [chamando um serviço WCF de um fluxo de trabalho em um projeto Web](http://go.microsoft.com/fwlink/?LinkId=207725).</span><span class="sxs-lookup"><span data-stu-id="e8e91-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="e8e91-109">Adicionando referências de serviço de dois ou mais serviços que contêm o mesmo nome de operação fará com que um problema.</span><span class="sxs-lookup"><span data-stu-id="e8e91-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="e8e91-110">As atividades geradas chamará somente a primeira operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="e8e91-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="e8e91-111">Para contornar esse problema renomear as operações de serviço para que eles são diferentes, ou alterar o nome da configuração de ponto de extremidade dentro de cada atividade gerado.</span><span class="sxs-lookup"><span data-stu-id="e8e91-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e91-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8e91-112">See Also</span></span>  
 [<span data-ttu-id="e8e91-113">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e8e91-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="e8e91-114">Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e8e91-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="e8e91-115">Chamando um serviço WCF de um fluxo de trabalho em um projeto Web</span><span class="sxs-lookup"><span data-stu-id="e8e91-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
