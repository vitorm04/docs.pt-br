---
title: Usar anotação em consultas
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 728408e744bc1eca62158fab1a7a17e985fe3b6c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69947281"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="ebe58-102">Usar anotação em consultas</span><span class="sxs-lookup"><span data-stu-id="ebe58-102">Using Annotation in Queries</span></span>
<span data-ttu-id="ebe58-103">As anotações permitem que você marca arbitrariamente registros de rastreamento com um valor que pode ser configurado após tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ebe58-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="ebe58-104">Por exemplo, talvez você queira que vários registros de acompanhamento em vários fluxos de trabalho sejam marcados com "servidor de email" = = "Server1 de email".</span><span class="sxs-lookup"><span data-stu-id="ebe58-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="ebe58-105">Isso facilita localizar todos os registros com essa marca ao consultar o rastreamento registra posteriormente.</span><span class="sxs-lookup"><span data-stu-id="ebe58-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="ebe58-106">Adicionando anotações</span><span class="sxs-lookup"><span data-stu-id="ebe58-106">Adding Annotations</span></span>  
 <span data-ttu-id="ebe58-107">Uma anotação pode ser adicionada a uma consulta de controle, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebe58-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="ebe58-108">Esses elementos de consulta de controle podem ser usados para criar um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ebe58-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="ebe58-109">Um perfil de rastreamento pode ser criado na configuração ou usando código.</span><span class="sxs-lookup"><span data-stu-id="ebe58-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe58-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="ebe58-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [<span data-ttu-id="ebe58-111">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ebe58-111">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ebe58-112">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ebe58-112">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
