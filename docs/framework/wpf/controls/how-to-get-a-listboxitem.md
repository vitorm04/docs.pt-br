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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910319"
---
# <a name="how-to-get-a-listboxitem"></a><span data-ttu-id="a3a58-102">Como: Obter um ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="a3a58-102">How to: Get a ListBoxItem</span></span>
<span data-ttu-id="a3a58-103">Se você precisar obter um determinado <xref:System.Windows.Controls.ListBoxItem> em um índice específico em um <xref:System.Windows.Controls.ListBox>, você pode usar um <xref:System.Windows.Controls.ItemContainerGenerator>.</span><span class="sxs-lookup"><span data-stu-id="a3a58-103">If you need to get a specific <xref:System.Windows.Controls.ListBoxItem> at a particular index in a <xref:System.Windows.Controls.ListBox>, you can use an <xref:System.Windows.Controls.ItemContainerGenerator>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a58-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3a58-104">Example</span></span>  
 <span data-ttu-id="a3a58-105">A exemplo a seguir mostra um <xref:System.Windows.Controls.ListBox> e seus itens.</span><span class="sxs-lookup"><span data-stu-id="a3a58-105">The following example shows a <xref:System.Windows.Controls.ListBox> and its items.</span></span>  
  
 [!code-xaml[ListBoxItems#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a3a58-106">O exemplo a seguir mostra como recuperar o item especificando o índice do item na <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> propriedade do <xref:System.Windows.Controls.ItemContainerGenerator>.</span><span class="sxs-lookup"><span data-stu-id="a3a58-106">The following example shows how to retrieve the item by specifying the index of the item in the <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> property of the <xref:System.Windows.Controls.ItemContainerGenerator>.</span></span>  
  
 [!code-csharp[ListBoxItems#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="a3a58-107">Depois de recuperar o item de caixa de listagem, você pode exibir o conteúdo do item, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3a58-107">After you have retrieved the list box item, you can display the contents of the item, as shown in the following example.</span></span>  
  
 [!code-csharp[ListBoxItems#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
