---
title: 'Como: Obter um ListBoxItem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
ms.openlocfilehash: 27a435feb4a941c77af221ab25bd63ea98b16e92
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360492"
---
# <a name="how-to-get-a-listboxitem"></a>Como: Obter um ListBoxItem
Se você precisar obter um determinado <xref:System.Windows.Controls.ListBoxItem> em um índice específico em um <xref:System.Windows.Controls.ListBox>, você pode usar um <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um <xref:System.Windows.Controls.ListBox> e seus itens.  
  
 [!code-xaml[ListBoxItems#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir mostra como recuperar o item especificando o índice do item na <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> propriedade do <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
 [!code-csharp[ListBoxItems#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 Depois de recuperar o item de caixa de listagem, você pode exibir o conteúdo do item, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[ListBoxItems#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
