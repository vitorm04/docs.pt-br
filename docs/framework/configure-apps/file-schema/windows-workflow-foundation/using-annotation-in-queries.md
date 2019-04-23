---
title: Usar anotação em consultas
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: fd2d98852ca44e3485ddcf4be29d505b39011698
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208638"
---
# <a name="using-annotation-in-queries"></a>Usar anotação em consultas
As anotações permitem que você marca arbitrariamente registros de rastreamento com um valor que pode ser configurado após tempo de compilação. Por exemplo, você pode querer vários registros de rastreamento em vários fluxos de trabalho a ser marcado com "Servidor" = = "Email Server1". Isso facilita localizar todos os registros com essa marca ao consultar o rastreamento registra posteriormente.  
  
## <a name="adding-annotations"></a>Adicionando anotações  
 Uma anotação pode ser adicionada a uma consulta de controle, conforme mostrado no exemplo a seguir.  
  
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
>  Esses elementos de consulta de controle podem ser usados para criar um perfil de rastreamento. Um perfil de rastreamento pode ser criado na configuração ou usando código.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
