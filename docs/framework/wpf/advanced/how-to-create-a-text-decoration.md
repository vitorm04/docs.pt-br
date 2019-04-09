---
title: 'Como: Criar uma decoração de texto'
ms.date: 03/30/2017
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
ms.openlocfilehash: d586eef8d1308070da38a0a54c63c3ba64d30c8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133829"
---
# <a name="how-to-create-a-text-decoration"></a>Como: Criar uma decoração de texto
Um <xref:System.Windows.TextDecoration> objeto é um Ornamento visual que você pode adicionar ao texto. Há quatro tipos de decoração de texto: sublinhado, linha de base, tachado e linha sobreposta. O exemplo a seguir mostra os locais das decorações de texto em relação ao texto.  
  
 ![Diagrama de tipos de decoração de texto](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Para adicionar uma decoração de texto ao texto, crie um <xref:System.Windows.TextDecoration> do objeto e modifique suas propriedades. Use o <xref:System.Windows.TextDecoration.Location%2A> propriedade para especificar onde a decoração de texto aparece, como sublinhado. Use o <xref:System.Windows.TextDecoration.Pen%2A> propriedade para especificar a aparência da decoração do texto, como um preenchimento sólido ou a cor do gradiente. Se você não especificar um valor para o <xref:System.Windows.TextDecoration.Pen%2A> propriedade, os padrões de decoração para a mesma cor do texto. Depois que você tiver definido uma <xref:System.Windows.TextDecoration> do objeto, adicione-o para o <xref:System.Windows.TextDecorations> coleção do objeto texto desejado.  
  
 O exemplo a seguir mostra uma decoração de texto que foi estilizada com um pincel de gradiente linear e uma caneta tracejada.  
  
 ![Decoração de texto com sublinhado de gradiente linear](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de fluxo de nível embutido que permite hospedar hiperlinks dentro do conteúdo de fluxo. Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado. <xref:System.Windows.TextDecoration> objetos podem ser desempenho intenso para instanciar, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos. Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar a mostrar um sublinhado somente ao disparar um evento, como o <xref:System.Windows.ContentElement.MouseEnter> eventos.  
  
 No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico — ele aparece somente quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.  
  
 ![Hiperlinks exibindo TextDecorations](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 Para obter mais informações, consulte [Especificar se um hiperlink está sublinhado](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo de código a seguir, uma decoração de texto sublinhado usa o valor de fonte padrão.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 No exemplo de código a seguir, uma decoração de texto sublinhado é criada com um pincel de cor sólida para a caneta.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 No exemplo de código a seguir, uma decoração de texto sublinhado é criada com um pincel de gradiente linear para a caneta tracejada.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Especificar se um hiperlink está sublinhado](how-to-specify-whether-a-hyperlink-is-underlined.md)
