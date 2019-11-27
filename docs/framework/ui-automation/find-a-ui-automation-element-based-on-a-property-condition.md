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
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433594"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico contém um código de exemplo que mostra como localizar um elemento dentro da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] com base em uma propriedade ou propriedades específicas.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, são especificados um conjunto de condições de propriedade que identificam um determinado elemento (ou elementos) de interesse na árvore de <xref:System.Windows.Automation.AutomationElement>. Uma pesquisa por todos os elementos correspondentes é então executada com o método <xref:System.Windows.Automation.AutomationElement.FindAll%2A> que incorpora uma série de <xref:System.Windows.Automation.AndCondition> operações boolianas para limitar o número de elementos correspondentes.  
  
> [!NOTE]
> Ao pesquisar no <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, você deve tentar obter apenas os filhos diretos. Uma pesquisa por descendentes pode iterar por centenas ou até milhares de elementos, possivelmente resultando em um estouro de pilha. Se você estiver tentando obter um elemento específico em um nível inferior, deverá iniciar a pesquisa na janela do aplicativo ou em um contêiner em um nível inferior.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplo de item de menu InvokePattern e ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [Obtendo elementos de automação de interface do usuário](obtaining-ui-automation-elements.md)
- [Usar a propriedade AutomationID](use-the-automationid-property.md)
