---
title: Usando uma atividade personalizada
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 6ca67ef7a8c4330d0182e960fc3fdcce656976a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962219"
---
# <a name="using-a-custom-activity"></a>Usando uma atividade personalizada
As atividades que derivam de <xref:System.Activities.Activity> ou suas subclasses podem ser compostas em fluxos de trabalho maiores ou criadas diretamente no código. Este tópico descreve como usar atividades personalizadas em fluxos de trabalho criados no código ou no designer.  
  
> [!NOTE]
> As atividades personalizadas podem ser usadas no mesmo projeto no qual elas são definidas, desde que a atividade personalizada e a atividade que as utiliza sejam compiladas (ou seja, carregadas por um tipo de instanciação gerado pelo processo de compilação) se a atividade de referência for carregada dinamicamente (por exemplo, usando ActivityXamlServices encontraram), o assembly referenciado deve ser colocado em um projeto diferente ou o XAML gerado pelo designer precisa ser editado manualmente para habilitar isso.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Usando uma atividade personalizada para um projeto de fluxo de trabalho  
  
1. Adicione uma referência do projeto de host para o projeto de biblioteca de atividade que contém a atividade personalizada.  
  
2. Compile a solução.  
  
3. Para usar a atividade personalizada no designer, localize a atividade personalizada na caixa de ferramentas e arraste a atividade na superfície do designer.  
  
4. Para usar a atividade personalizada no código, adicione uma instrução Using que se refere ao projeto de atividade personalizada, e transmita uma nova instância da atividade para <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
