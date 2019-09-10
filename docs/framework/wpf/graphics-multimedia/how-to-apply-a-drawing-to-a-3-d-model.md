---
title: 'Como: Aplicar um desenho a um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855872"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Como: Aplicar um desenho a um modelo 3D

Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> como aplicado a um modelo 3D.

O código a seguir define <xref:System.Windows.Media.DrawingGroup> um como o conteúdo de <xref:System.Windows.Media.DrawingBrush>um.  O <xref:System.Windows.Media.DrawingBrush> é definido como a <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriedade de <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um plano 3D.

> [!NOTE]
> Geralmente, é desejável definir objetos e valores complexos, como o desenho abaixo, como recursos que podem ser reutilizados e simplificar seu código. Consulte [recursos XAML](../advanced/xaml-resources.md) para obter mais informações.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Exemplo

O código a seguir mostra a amostra inteira.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Consulte também

- [Recursos XAML](../advanced/xaml-resources.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
