---
title: 'Como: Criar uma cena 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112096"
---
# <a name="how-to-create-a-3d-scene"></a>Como: Criar uma cena 3D
Este exemplo mostra como criar um objeto 3D que se parece com uma folha plana de papel que foi girada. Juntamente <xref:System.Windows.Controls.Viewport3D> com os seguintes componentes são usados para criar esta simples cena 3D:  
  
- Uma câmera é criada <xref:System.Windows.Media.Media3D.PerspectiveCamera>usando um . A câmera especifica qual parte da cena 3D é visível.  
  
- Uma malha é criada para especificar a forma do objeto <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> 3D (folha de papel) usando a propriedade de <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Um material é especificado para ser exibido na superfície do objeto (gradiente linear nesta amostra) usando a <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade de <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Uma luz é criada para brilhar <xref:System.Windows.Media.Media3D.DirectionalLight>sobre o objeto usando .  
  
## <a name="example"></a>Exemplo  
 O código abaixo mostra como criar uma cena 3D em XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 O código abaixo mostra como criar a mesma cena 3D no código processual.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
