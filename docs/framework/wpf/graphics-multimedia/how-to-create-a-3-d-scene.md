---
title: Como criar uma cena 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559520"
---
# <a name="how-to-create-a-3-d-scene"></a>Como criar uma cena 3D
Este exemplo mostra como criar um objeto 3D parecido com uma folha de papel que foi girada. Um <xref:System.Windows.Controls.Viewport3D> juntamente com os seguintes componentes são usados para criar esta cena 3D simples:  
  
-   Uma câmera é criada usando um <xref:System.Windows.Media.Media3D.PerspectiveCamera>. A câmera especifica qual parte da cena 3D é visível.  
  
-   Uma malha é criada para especificar a forma do objeto 3D (folha de papel) usando o <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriedade <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Um material é especificado para ser exibido na superfície do objeto (gradiente linear neste exemplo) usando o <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   A luz é criada para ser exibido no objeto usando <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como criar uma cena 3D em XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como criar a mesma cena 3D em código procedural.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
