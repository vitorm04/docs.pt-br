---
title: "Como especificar se um hiperlink está sublinhado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24c3cc1bba4fd12d4a0f2ad02fa0c1b52b124381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Como especificar se um hiperlink está sublinhado
O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de nível interno que permite a hiperlinks dentro do conteúdo de fluxo. Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado. <xref:System.Windows.TextDecoration>os objetos podem ser desempenho intensivo para criar uma instância, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos. Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar mostrar um sublinhado somente quando ativando um evento, tal como o <xref:System.Windows.ContentElement.MouseEnter> evento.  
  
 No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico, ele aparece apenas quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.  
  
 ![Hiperlinks exibindo TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hiperlinks definidos com TextDecorations  
  
## <a name="example"></a>Exemplo  
 O exemplo de marcação a seguir mostra um <xref:System.Windows.Documents.Hyperlink> definido com e sem sublinhado:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 O exemplo de código a seguir mostra como criar um sublinhado para o <xref:System.Windows.Documents.Hyperlink> no <xref:System.Windows.ContentElement.MouseEnter> evento e removê-lo no <xref:System.Windows.ContentElement.MouseLeave> evento.  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Criar uma decoração de texto](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
