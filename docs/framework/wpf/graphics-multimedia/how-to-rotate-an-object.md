---
title: Como girar um objeto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112057"
---
# <a name="how-to-rotate-an-object"></a>Como girar um objeto
Este exemplo mostra como girar um objeto. O exemplo primeiro <xref:System.Windows.Media.RotateTransform> cria a <xref:System.Windows.Media.RotateTransform.Angle%2A> e, em seguida, especifica seu em graus.  
  
 O exemplo a <xref:System.Windows.Shapes.Polyline> seguir gira um objeto de 45 graus sobre seu canto superior esquerdo.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 As <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> especificar o ponto sobre o qual o objeto é girado. Esse ponto central é expresso no espaço coordenado do elemento que é transformado. Por padrão, a rotação é aplicada a (0,0), que é o canto superior esquerdo do objeto a ser transformado.  
  
 O próximo exemplo <xref:System.Windows.Shapes.Polyline> gira um objeto no sentido horário 45 graus sobre o ponto (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 A ilustração a seguir mostra <xref:System.Windows.Media.Transform> os resultados da aplicação de um aos dois objetos.  
  
 ![Rotações de 45 graus com pontos centrais diferentes](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dois objetos que giram 45 graus de diferentes centros de rotação  
  
 Os <xref:System.Windows.Shapes.Polyline> exemplos anteriores são <xref:System.Windows.UIElement>um . Quando você <xref:System.Windows.Media.Transform> aplica <xref:System.Windows.UIElement.RenderTransform%2A> um à <xref:System.Windows.UIElement>propriedade de <xref:System.Windows.UIElement.RenderTransformOrigin%2A> um , você pode <xref:System.Windows.Media.Transform> usar a propriedade para especificar uma origem para cada que você aplica ao elemento. Como <xref:System.Windows.UIElement.RenderTransformOrigin%2A> a propriedade usa coordenadas relativas, você pode aplicar uma transformação ao centro do elemento mesmo que você não saiba o seu tamanho. Para obter mais informações e por exemplo, consulte [Especificar a Origem de uma Transformação usando valores relativos](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Para obter a amostra completa, consulte [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Transform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de como fazer](transformations-how-to-topics.md)
