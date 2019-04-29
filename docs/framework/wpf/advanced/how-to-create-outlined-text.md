---
title: 'Como: Criar texto contornado'
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
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776700"
---
# <a name="how-to-create-outlined-text"></a>Como: Criar texto contornado
Na maioria dos casos, ao adicionar ornamentos a cadeias de caracteres de texto em seu aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], você está usando texto em termos de uma coleção de caracteres separados ou glifos. Por exemplo, você poderia criar um pincel de gradiente linear e aplicá-lo para o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.TextBox> objeto. Ao exibir ou editar a caixa de texto, o pincel de gradiente linear é aplicado automaticamente ao conjunto de caracteres atual na cadeia de texto.  
  
 ![Texto exibido com um pincel de gradiente linear](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 No entanto, você também pode converter texto em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de texto visualmente atrativo. Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Quando o texto é convertido em um <xref:System.Windows.Media.Geometry> do objeto, ele não é mais um conjunto de caracteres — você não pode modificar os caracteres na cadeia de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido.  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais modificando o traço e o preenchimento do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Também é possível modificar o retângulo da caixa delimitadora ou realce, do texto convertido. O exemplo a seguir ilustra uma maneira de criar efeitos visuais modificando o traço e realce do texto convertido.  
  
 ![Texto com pincel de imagem aplicado para traçar e realce](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Exemplo  
 A chave para converter texto em uma <xref:System.Windows.Media.Geometry> objeto é usar o <xref:System.Windows.Media.FormattedText> objeto. Depois de criar esse objeto, você pode usar o <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> e <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> métodos para converter o texto a ser <xref:System.Windows.Media.Geometry> objetos. O primeiro método retorna a geometria do texto formatado; o segundo método retorna a geometria da caixa delimitadora do texto formatado. O exemplo de código a seguir mostra como criar um <xref:System.Windows.Media.FormattedText> objeto e recuperar as geometrias do texto formatado e da caixa delimitadora.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Para exibir o recuperado o <xref:System.Windows.Media.Geometry> objetos, você precisa acessar o <xref:System.Windows.Media.DrawingContext> do objeto que está exibindo o texto convertido. Nesses exemplos de código, isso é feito criando um objeto de controle personalizado derivado de uma classe que dá suporte a renderização definida pelo usuário.  
  
 Para exibir <xref:System.Windows.Media.Geometry> objetos no controle personalizado, forneça uma substituição para o <xref:System.Windows.UIElement.OnRender%2A> método. O método substituído deve usar o <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> método para desenhar o <xref:System.Windows.Media.Geometry> objetos.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Para a fonte do objeto de controle de usuário personalizada de exemplo, consulte [OutlineTextControl.cs para C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) e [OutlineTextControl.vb para o Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb). 
  
## <a name="see-also"></a>Consulte também

- [Desenhando texto formatado](drawing-formatted-text.md)
