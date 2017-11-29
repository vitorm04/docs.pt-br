---
title: "Usando a anotação em consultas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8713d84af96fa69df5ace33d76ec21560dab2c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="3f0e5-102">Usando a anotação em consultas</span><span class="sxs-lookup"><span data-stu-id="3f0e5-102">Using Annotation in Queries</span></span>
<span data-ttu-id="3f0e5-103">As anotações permitem que você marca arbitrariamente registros de rastreamento com um valor que pode ser configurado após tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="3f0e5-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="3f0e5-104">Por exemplo, convém vários registros de rastreamento em vários fluxos de trabalho sejam marcados com "Servidor de email" = = "Email Server1".</span><span class="sxs-lookup"><span data-stu-id="3f0e5-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="3f0e5-105">Isso facilita localizar todos os registros com essa marca ao consultar o rastreamento registra posteriormente.</span><span class="sxs-lookup"><span data-stu-id="3f0e5-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="3f0e5-106">Adicionando anotações</span><span class="sxs-lookup"><span data-stu-id="3f0e5-106">Adding Annotations</span></span>  
 <span data-ttu-id="3f0e5-107">Uma anotação pode ser adicionada a uma consulta de controle, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3f0e5-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
>  <span data-ttu-id="3f0e5-108">Esses elementos de consulta de controle podem ser usados para criar um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3f0e5-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="3f0e5-109">Um perfil de rastreamento pode ser criado na configuração ou usando código.</span><span class="sxs-lookup"><span data-stu-id="3f0e5-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0e5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f0e5-110">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="3f0e5-111">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="3f0e5-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [<span data-ttu-id="3f0e5-112">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3f0e5-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="3f0e5-113">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3f0e5-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
