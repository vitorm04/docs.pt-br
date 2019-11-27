---
title: Invocando um Controle Utilizando Automação de IU
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447007"
---
# <a name="invoke-a-control-using-ui-automation"></a>Invocando um Controle Utilizando Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico demonstra como executar as seguintes tarefas:  
  
- Localize um controle que corresponda a condições de propriedade específicas percorrendo a exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para o aplicativo de destino.  
  
- Crie um <xref:System.Windows.Automation.AutomationElement> para cada controle.  
  
- Obtenha um objeto <xref:System.Windows.Automation.InvokePattern> de qualquer elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] encontrado que dê suporte ao padrão de controle de <xref:System.Windows.Automation.InvokePattern>.  
  
- Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> para invocar o controle de um manipulador de eventos de cliente.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o método <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> da classe <xref:System.Windows.Automation.AutomationElement> para gerar um objeto <xref:System.Windows.Automation.InvokePattern> e invocar um controle usando o método <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplo de InvokePattern, ExpandCollapsePattern e TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
