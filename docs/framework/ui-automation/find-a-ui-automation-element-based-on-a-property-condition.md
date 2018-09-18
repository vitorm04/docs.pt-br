---
title: Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4c4f14f79960b98618a4f6a3450b1e1a2c05f731
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003536"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico contém código de exemplo que mostra como localizar um elemento dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore com base em uma ou mais propriedades específicas.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um conjunto de condições de propriedade é especificado para identificar um determinado elemento (ou elementos) de seu interesse no <xref:System.Windows.Automation.AutomationElement> árvore. Em seguida, é executada uma pesquisa por todos os elementos correspondentes com o <xref:System.Windows.Automation.AutomationElement.FindAll%2A> método que incorpora uma série de <xref:System.Windows.Automation.AndCondition> operações booleanas para limitar o número de elementos correspondentes.  
  
> [!NOTE]
>  Ao pesquisar a partir de <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, você deve tentar obter apenas os filhos diretos. Uma pesquisa por descendentes pode percorrer centenas ou mesmo milhares de elementos, possivelmente resultando em um estouro de pilha. Se você está tentando obter um elemento específico em um nível inferior, você deve iniciar a pesquisa de janela do aplicativo ou de um contêiner em um nível inferior.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de Item de Menu ExpandCollapsePattern e InvokePattern](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [Obtendo elementos de automação de interface do usuário](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [Usar a propriedade AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md)
