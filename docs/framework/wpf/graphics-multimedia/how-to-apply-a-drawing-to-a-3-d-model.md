---
title: Como aplicar um desenho a um modelo 3D
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459372"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Como aplicar um desenho a um modelo 3D

Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> como o <xref:System.Windows.Media.Media3D.Material> aplicado a um modelo 3D.

O código a seguir define um <xref:System.Windows.Media.DrawingGroup> como o conteúdo de um <xref:System.Windows.Media.DrawingBrush>.  O <xref:System.Windows.Media.DrawingBrush> é definido como a propriedade <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> do <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um plano 3D.

> [!NOTE]
> Geralmente, é desejável definir objetos e valores complexos, como o desenho abaixo, como recursos que podem ser reutilizados e simplificar seu código. Consulte [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) para obter mais informações.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Exemplo

O código a seguir mostra a amostra inteira.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Consulte também

- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
