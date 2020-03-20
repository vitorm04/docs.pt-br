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
ms.openlocfilehash: d0ce46b9895589fd4635b567136204368a6431ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186865"
---
# <a name="how-to-create-outlined-text"></a>Como criar texto de estrutura de tópicos
Na maioria dos casos, ao adicionar ornamentos a cadeias de caracteres de texto em seu aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], você está usando texto em termos de uma coleção de caracteres separados ou glifos. Por exemplo, você pode criar um pincel de <xref:System.Windows.Controls.Control.Foreground%2A> gradiente <xref:System.Windows.Controls.TextBox> linear e aplicá-lo à propriedade de um objeto. Ao exibir ou editar a caixa de texto, o pincel de gradiente linear é aplicado automaticamente ao conjunto de caracteres atual na cadeia de texto.  
  
 ![Texto exibido com um pincel de gradiente linear](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 No entanto, você <xref:System.Windows.Media.Geometry> também pode converter texto em objetos, permitindo que você crie outros tipos de texto visualmente rico. Por exemplo, você <xref:System.Windows.Media.Geometry> pode criar um objeto com base no contorno de uma seqüência de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Quando o texto é <xref:System.Windows.Media.Geometry> convertido em um objeto, ele não é mais uma coleção de caracteres — você não pode modificar os caracteres na seqüência de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido.  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais modificando o traço e o preenchimento do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Também é possível modificar o retângulo da caixa delimitadora ou realce, do texto convertido. O exemplo a seguir ilustra uma maneira de criar efeitos visuais modificando o traço e realce do texto convertido.  
  
 ![Texto com pincel de imagem aplicado ao traçado e destaque](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Exemplo  
 A chave para converter <xref:System.Windows.Media.Geometry> texto em um <xref:System.Windows.Media.FormattedText> objeto é usar o objeto. Depois de criar esse objeto, você <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> pode usar os métodos e métodos para converter o texto em <xref:System.Windows.Media.Geometry> objetos. O primeiro método retorna a geometria do texto formatado; o segundo método retorna a geometria da caixa delimitadora do texto formatado. O exemplo de código a <xref:System.Windows.Media.FormattedText> seguir mostra como criar um objeto e recuperar as geometrias do texto formatado e sua caixa delimitadora.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Para exibir os <xref:System.Windows.Media.Geometry> objetos recuperados, você precisa <xref:System.Windows.Media.DrawingContext> acessar o objeto que está exibindo o texto convertido. Nesses exemplos de código, isso é feito criando um objeto de controle personalizado derivado de uma classe que dá suporte a renderização definida pelo usuário.  
  
 Para <xref:System.Windows.Media.Geometry> exibir objetos no controle personalizado, <xref:System.Windows.UIElement.OnRender%2A> forneça uma substituição para o método. Seu método substituído deve <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> usar o <xref:System.Windows.Media.Geometry> método para desenhar os objetos.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Para obter a origem do exemplo do objeto de controle personalizado do usuário, consulte [OutlineTextControl.cs para C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) e [OutlineTextControl.vb para Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).
  
## <a name="see-also"></a>Confira também

- [Desenhando texto formatado](drawing-formatted-text.md)
