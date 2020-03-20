---
title: Como criar uma decoração de texto
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
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185930"
---
# <a name="how-to-create-a-text-decoration"></a>Como criar uma decoração de texto
Um <xref:System.Windows.TextDecoration> objeto é uma ornamentação visual que você pode adicionar ao texto. Há quatro tipos de decoração de texto: sublinhado, linha de base, tachado e linha sobreposta. O exemplo a seguir mostra os locais das decorações de texto em relação ao texto.  
  
 ![Diagrama de tipos de decoração de texto](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Para adicionar uma decoração de <xref:System.Windows.TextDecoration> texto ao texto, crie um objeto e modifique suas propriedades. Use <xref:System.Windows.TextDecoration.Location%2A> a propriedade para especificar onde a decoração do texto aparece, como sublinhar. Use <xref:System.Windows.TextDecoration.Pen%2A> a propriedade para especificar a aparência da decoração do texto, como um preenchimento sólido ou cor gradiente. Se você não especificar <xref:System.Windows.TextDecoration.Pen%2A> um valor para a propriedade, a decoração será padrão para a mesma cor do texto. Depois de definir <xref:System.Windows.TextDecoration> um objeto, <xref:System.Windows.TextDecorations> adicione-o à coleção do objeto de texto desejado.  
  
 O exemplo a seguir mostra uma decoração de texto que foi estilizada com um pincel de gradiente linear e uma caneta tracejada.  
  
 ![Decoração de texto com sublinhado em gradiente linear](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de fluxo de nível inline que permite hospedar hiperlinks dentro do conteúdo de fluxo. Por padrão, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.TextDecoration> usa um objeto para exibir um sublinhado. <xref:System.Windows.TextDecoration>objetos podem ser intensivos em desempenho <xref:System.Windows.Documents.Hyperlink> para instanciar, especialmente se você tiver muitos objetos. Se você fizer <xref:System.Windows.Documents.Hyperlink> uso extensivo de elementos, você pode considerar mostrar um <xref:System.Windows.ContentElement.MouseEnter> sublinhado apenas ao desencadear um evento, como o evento.  
  
 No exemplo a seguir, o sublinhado para o link "Meu MSN" é dinâmico — ele só aparece quando o <xref:System.Windows.ContentElement.MouseEnter> evento é acionado.  
  
 ![Hiperlinks que exibem TextDecorations](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

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
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Especificar se um hiperlink está sublinhado](how-to-specify-whether-a-hyperlink-is-underlined.md)
