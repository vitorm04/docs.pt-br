---
title: 'Como: Melhorar o desempenho de rolagem de um ListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770858"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Como: Melhorar o desempenho de rolagem de um ListBox
Se um <xref:System.Windows.Controls.ListBox> contém muitos itens, a resposta de interface do usuário pode ser lenta quando o usuário rola a <xref:System.Windows.Controls.ListBox> usando a roda do mouse ou arrastando o controle de posição de uma barra de rolagem. Você pode melhorar o desempenho do <xref:System.Windows.Controls.ListBox> quando o usuário rola, definindo o `VirtualizingStackPanel.VirtualizationMode` anexado à propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
O exemplo a seguir cria uma <xref:System.Windows.Controls.ListBox> e define o `VirtualizingStackPanel.VirtualizationMode` anexado à propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> para melhorar o desempenho durante a rolagem.  
  
## <a name="code"></a>Código  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 O exemplo a seguir mostra os dados que o exemplo anterior usa.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
