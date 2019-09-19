---
title: Navegar em elementos de automação de interface do usuário com TreeWalker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: 7ecf6edd37b656f7dd1d7e31506d0dd455592d9b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042976"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>Navegar em elementos de automação de interface do usuário com TreeWalker
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico contém um código de exemplo que mostra como navegar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] entre elementos usando a <xref:System.Windows.Automation.TreeWalker> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir <xref:System.Windows.Automation.TreeWalker.GetParent%2A> usa para percorrer a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] árvore até encontrar o elemento raiz ou área de trabalho. O elemento logo abaixo dessa é a janela pai do elemento especificado.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> usa <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> e para criar <xref:System.Windows.Forms.TreeView> um que mostra uma subárvore [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] inteira de elementos que estão no modo de exibição de controle e que estão habilitados.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Consulte também

- [Obtendo elementos de automação de interface do usuário](obtaining-ui-automation-elements.md)
