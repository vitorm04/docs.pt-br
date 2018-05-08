---
title: Como criar texto de estrutura de tópicos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: c79f5c1c6812b1175119133664e39995af29bd4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-outlined-text"></a>Como criar texto de estrutura de tópicos
Na maioria dos casos, ao adicionar ornamentos a cadeias de caracteres de texto em seu aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], você está usando texto em termos de uma coleção de caracteres separados ou glifos. Por exemplo, você pode criar um pincel de gradiente linear e aplicá-lo a <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.TextBox> objeto. Ao exibir ou editar a caixa de texto, o pincel de gradiente linear é aplicado automaticamente ao conjunto de caracteres atual na cadeia de texto.  
  
 ![Texto exibido com um pincel de gradiente linear](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
Exemplo de um pincel de gradiente linear aplicado a uma caixa de texto  
  
 No entanto, você também pode converter texto em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de visualmente rich text. Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.  
  
 ![Estrutura de tópicos de texto usando um pincel de gradiente linear](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Exemplo de um pincel de gradiente linear aplicado à geometria de contorno do texto  
  
 Quando o texto é convertido em um <xref:System.Windows.Media.Geometry> do objeto, ele não é mais um conjunto de caracteres — você não pode modificar os caracteres na cadeia de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido.  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais modificando o traço e o preenchimento do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Exemplo de configuração de borda e preenchimento com diferentes cores.  
  
 ![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Exemplo de um pincel de imagem aplicado ao traço  
  
 Também é possível modificar o retângulo da caixa delimitadora ou realce, do texto convertido. O exemplo a seguir ilustra uma maneira de criar efeitos visuais modificando o traço e realce do texto convertido.  
  
 ![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Exemplo de um pincel de imagem aplicado ao traço e ao realce  
  
## <a name="example"></a>Exemplo  
 A chave para converter texto em uma <xref:System.Windows.Media.Geometry> objeto é usar o <xref:System.Windows.Media.FormattedText> objeto. Depois de criar esse objeto, você pode usar o <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> e <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> métodos para converter o texto a ser <xref:System.Windows.Media.Geometry> objetos. O primeiro método retorna a geometria do texto formatado; o segundo método retorna a geometria da caixa delimitadora do texto formatado. O exemplo de código a seguir mostra como criar um <xref:System.Windows.Media.FormattedText> objeto e recuperar as geometrias do texto formatado e da caixa delimitadora.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Para exibir recuperada a <xref:System.Windows.Media.Geometry> objetos, você precisa acessar o <xref:System.Windows.Media.DrawingContext> do objeto que está exibindo o texto convertido. Nesses exemplos de código, isso é feito criando um objeto de controle personalizado derivado de uma classe que dá suporte a renderização definida pelo usuário.  
  
 Para exibir <xref:System.Windows.Media.Geometry> objetos no controle personalizado, fornecer uma substituição para o <xref:System.Windows.UIElement.OnRender%2A> método. O método sobrescrito deve usar o <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> método para desenhar o <xref:System.Windows.Media.Geometry> objetos.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a>Consulte também  
 [Desenhando texto formatado](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
