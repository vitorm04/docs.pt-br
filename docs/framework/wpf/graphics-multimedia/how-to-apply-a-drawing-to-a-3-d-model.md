---
title: 'Como: Aplicar um desenho a um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112174"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>Como: Aplicar um desenho a um modelo 3D

Este exemplo mostra como <xref:System.Windows.Media.DrawingBrush> usar <xref:System.Windows.Media.Media3D.Material> um como o aplicado a um modelo 3D.

O código a <xref:System.Windows.Media.DrawingGroup> seguir define a <xref:System.Windows.Media.DrawingBrush>como o conteúdo de a .  O <xref:System.Windows.Media.DrawingBrush> é definido <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> como <xref:System.Windows.Media.Media3D.DiffuseMaterial> propriedade do aplicado a um plano 3D.

> [!NOTE]
> Muitas vezes é desejável definir objetos e valores complexos como o desenho abaixo como recursos que podem ser reutilizados e simplificar seu código. Consulte [os recursos xaml](../../../desktop-wpf/fundamentals/xaml-resources-define.md) para obter mais informações.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Exemplo

O código a seguir mostra toda a amostra.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Confira também

- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
