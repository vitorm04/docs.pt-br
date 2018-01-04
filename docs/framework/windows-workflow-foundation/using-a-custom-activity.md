---
title: Usando uma atividade personalizada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7558ca965af6cc9acd35ecab47bf9f66f592b15f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-custom-activity"></a>Usando uma atividade personalizada
As atividades que derivam de <xref:System.Activities.Activity> ou suas subclasses podem ser compostas em fluxos de trabalho maiores ou criadas diretamente no código. Este tópico descreve como usar atividades personalizadas em fluxos de trabalho criados no código ou no designer.  
  
> [!NOTE]
>  Atividades personalizadas podem ser usadas no mesmo projeto em que eles são definidos, desde que a atividade personalizada e a atividade que usa são compilados (ou seja, carregado por um tipo ao instanciar gerado pelo processo de compilação) se a atividade de referência é carregada dinamicamente (por exemplo, usando ActivityXAMLServices), em seguida, o assembly referenciado deve ser colocado em um projeto diferente ou gerado pelo designer XAML precisa ser editados manualmente para permitir isso.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Usando uma atividade personalizada para um projeto de fluxo de trabalho  
  
1.  Adicione uma referência do projeto de host para o projeto de biblioteca de atividade que contém a atividade personalizada.  
  
2.  Compile a solução.  
  
3.  Para usar a atividade personalizada no designer, localize a atividade personalizada na caixa de ferramentas e arraste a atividade na superfície do designer.  
  
4.  Para usar a atividade personalizada no código, adicione uma instrução Using que se refere ao projeto de atividade personalizada, e transmita uma nova instância da atividade para <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
