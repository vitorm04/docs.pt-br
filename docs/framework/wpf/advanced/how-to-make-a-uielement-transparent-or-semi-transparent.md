---
title: 'Como: Deixar um UIElement transparente ou semitransparente'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942864"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Como: Deixar um UIElement transparente ou semitransparente
Este exemplo mostra como fazer um <xref:System.Windows.UIElement> transparente ou semitransparente. Para tornar um elemento transparente ou semitransparente, defina seu <xref:System.Windows.UIElement.Opacity%2A> propriedade. Um valor de `0.0` torna o elemento completamente transparente, enquanto um valor de `1.0` torna o elemento completamente opaco. Um valor de `0.5` torna o elemento 50% opaco e assim por diante. Um elemento <xref:System.Windows.UIElement.Opacity%2A> é definido como `1.0` por padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o <xref:System.Windows.UIElement.Opacity%2A> de um botão para `0.25`, fazendo com ele e seu conteúdo (neste caso, o texto do botão) 25% opaco.  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Se o conteúdo de um elemento tiver suas próprias <xref:System.Windows.UIElement.Opacity%2A> configurações, esses valores serão multiplicadas nos elementos que contém <xref:System.Windows.UIElement.Opacity%2A>.  
  
 O exemplo a seguir define um botão <xref:System.Windows.UIElement.Opacity%2A> à `0.25`e o <xref:System.Windows.UIElement.Opacity%2A> de uma <xref:System.Windows.Controls.Image> controle contido no botão para `0.5`. Como resultado, a imagem aparece 12,5% opaca: 0.25 * 0.5 = 0.125.  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Outra maneira de controlar a opacidade de um elemento é definir a opacidade do <xref:System.Windows.Media.Brush> que pinta o elemento. Essa abordagem permite que você altere seletivamente a opacidade de partes de um elemento e fornece benefícios de desempenho com o uso do elemento <xref:System.Windows.UIElement.Opacity%2A> propriedade. O exemplo a seguir define o <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush> usado para pintar o botão <xref:System.Windows.Controls.Control.Background%2A> é definido como `0.25`. Como resultado, a tela de fundo do pincel é 25% opaca, mas seu conteúdo (o texto do botão) permanece 100% opaco.  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Também é possível controlar a opacidade de cores individuais em um pincel. Para obter mais informações sobre cores e pincéis, consulte [Visão geral de pintura com cores sólidas e gradientes](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Para ver um exemplo que mostra como animar a opacidade de um elemento, consulte [Animar a opacidade de um elemento ou pincel](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
