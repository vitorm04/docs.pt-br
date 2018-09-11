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
ms.openlocfilehash: b5a954158388e8b85589042e9d1f3b82c1747e30
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353795"
---
# <a name="how-to-rotate-an-object"></a>Como girar um objeto
Este exemplo mostra como girar um objeto. O exemplo cria primeiro um <xref:System.Windows.Media.RotateTransform> e, em seguida, especifica sua <xref:System.Windows.Media.RotateTransform.Angle%2A> em graus.  
  
 O exemplo a seguir gira um <xref:System.Windows.Shapes.Polyline> 45 graus sobre seu canto superior esquerdo do objeto.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 O <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> especificar o ponto sobre o qual o objeto é girado. Esse ponto central é expresso no espaço coordenado do elemento que é transformado. Por padrão, a rotação é aplicada a (0,0), que é o canto superior esquerdo do objeto a ser transformado.  
  
 O próximo exemplo gira um <xref:System.Windows.Shapes.Polyline> 45 graus no sentido horário em torno do ponto (25,50) do objeto.  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 A ilustração a seguir mostra os resultados da aplicação de um <xref:System.Windows.Media.Transform> aos dois objetos.  
  
 ![rotações de 45 graus com diferentes pontos centrais](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dois objetos que giram 45 graus de diferentes centros de rotação  
  
 O <xref:System.Windows.Shapes.Polyline> nos exemplos anteriores é um <xref:System.Windows.UIElement>. Quando você aplica um <xref:System.Windows.Media.Transform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de uma <xref:System.Windows.UIElement>, você pode usar os <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade para especificar uma origem para cada <xref:System.Windows.Media.Transform> aplicáveis ao elemento. Porque o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade usa coordenadas relativas, você pode aplicar uma transformação ao centro do elemento, mesmo se você não souber seu tamanho. Para obter mais informações e para obter um exemplo, consulte [especificar a origem de uma transformação usando valores relativos](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Transform>  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
