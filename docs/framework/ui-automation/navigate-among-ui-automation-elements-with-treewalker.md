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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 6a44cd16513bffa47e56064ea7e0e05692cb78a7
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44341729"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>Navegar em elementos de automação de interface do usuário com TreeWalker
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico contém código de exemplo que mostra como navegar entre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementos usando o <xref:System.Windows.Automation.TreeWalker> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Automation.TreeWalker.GetParent%2A> para percorrer o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] de árvore até que ele localiza o elemento raiz, ou a área de trabalho. O elemento logo abaixo que é a janela pai do elemento especificado.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> e <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> para criar um <xref:System.Windows.Forms.TreeView> que mostra uma subárvore inteira de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementos que estão no modo de exibição de controle e que estão habilitados.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Consulte também  
 [Obtendo elementos de automação de interface do usuário](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
