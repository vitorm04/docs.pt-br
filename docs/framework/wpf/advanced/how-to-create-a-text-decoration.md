---
title: "Como criar uma decoração de texto"
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
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0beb22ba78c6fc99951bc2d780c1c5defa32e637
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-text-decoration"></a>Como criar uma decoração de texto
Um <xref:System.Windows.TextDecoration> objeto é um Ornamento visual que você pode adicionar ao texto. Há quatro tipos de decoração de texto: sublinhado, linha de base, tachado e linha sobreposta. O exemplo a seguir mostra os locais da decoração de texto em relação ao texto.  
  
 ![Diagrama de locais de decoração de texto](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Exemplo de tipos de decoração de texto  
  
 Para adicionar uma decoração de texto em texto, crie um <xref:System.Windows.TextDecoration> de objeto e modificar suas propriedades. Use o <xref:System.Windows.TextDecoration.Location%2A> propriedade para especificar onde a decoração de texto aparece, como sublinhado. Use o <xref:System.Windows.TextDecoration.Pen%2A> propriedade para especificar a aparência da decoração do texto, como um preenchimento sólido ou a cor do gradiente. Se você não especificar um valor para o <xref:System.Windows.TextDecoration.Pen%2A> propriedade, os padrões de decoração para a mesma cor do texto. Depois que você tenha definido um <xref:System.Windows.TextDecoration> do objeto, adicione-o para o <xref:System.Windows.TextDecorations> coleção do objeto texto desejado.  
  
 O exemplo a seguir mostra uma decoração de texto que foi estilizada com um pincel de gradiente linear e uma caneta tracejada.  
  
 ![Decoração de texto com sublinhado em gradiente linear](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Exemplo de um sublinhado estilizado com um pincel de gradiente linear e uma caneta tracejada  
  
 O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de nível interno que permite a hiperlinks dentro do conteúdo de fluxo. Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado. <xref:System.Windows.TextDecoration>os objetos podem ser desempenho intensivo para criar uma instância, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos. Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar mostrar um sublinhado somente quando ativando um evento, tal como o <xref:System.Windows.ContentElement.MouseEnter> evento.  
  
 No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico, ele aparece apenas quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.  
  
 ![Hiperlinks exibindo TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hiperlinks definidos com TextDecorations  
  
 Para obter mais informações, consulte [Especificar se um hiperlink está sublinhado](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo de código a seguir, uma decoração de texto sublinhado usa o valor de fonte padrão.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 No exemplo de código a seguir, uma decoração de texto sublinhado é criada com um pincel de cor sólida para a caneta.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 No exemplo de código a seguir, uma decoração de texto sublinhado é criada com um pincel de gradiente linear para a caneta tracejada.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Especificar se um hiperlink está sublinhado](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
