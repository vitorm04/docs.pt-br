---
title: Como obter um ListBoxItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
ms.openlocfilehash: f1e25ce60ff5feb8fd644a5864dbd762b4b5fa39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552721"
---
# <a name="how-to-get-a-listboxitem"></a>Como obter um ListBoxItem
Se você precisar obter uma determinada <xref:System.Windows.Controls.ListBoxItem> em um índice específico em um <xref:System.Windows.Controls.ListBox>, você pode usar um <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um <xref:System.Windows.Controls.ListBox> e seus itens.  
  
 [!code-xaml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir mostra como recuperar o item especificando o índice do item no <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> propriedade o <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 Depois de recuperar o item da caixa de lista, você pode exibir o conteúdo do item, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
