---
title: 'Como: Transformar a escala de um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111979"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a><span data-ttu-id="079ab-102">Como: Transformar a escala de um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="079ab-102">How to: Transform the Scale of a 3D Model</span></span>
<span data-ttu-id="079ab-103">Este exemplo mostra como dimensionar um objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="079ab-103">This example shows how to scale a 3D object.</span></span> <span data-ttu-id="079ab-104">Para dimensionar um objeto <xref:System.Windows.Media.Media3D.ScaleTransform3D>3D, use um .</span><span class="sxs-lookup"><span data-stu-id="079ab-104">To scale a 3D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="079ab-105">As <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>propriedades <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> e propriedades redimensionam o elemento pelo fator especificado.</span><span class="sxs-lookup"><span data-stu-id="079ab-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="079ab-106">Por exemplo, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> um valor de 1,5 estende um objeto a 150% de sua largura original.</span><span class="sxs-lookup"><span data-stu-id="079ab-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="079ab-107">Um <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valor de 0,5 reduz a altura de um objeto em 50%.</span><span class="sxs-lookup"><span data-stu-id="079ab-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="079ab-108">O código abaixo <xref:System.Windows.Media.Media3D.ScaleTransform3D> mostra usando um <xref:System.Windows.Media.Media3D.GeometryModel3D>como a transformação para um .</span><span class="sxs-lookup"><span data-stu-id="079ab-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="079ab-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="079ab-109">Example</span></span>  
 <span data-ttu-id="079ab-110">O código a seguir mostra toda a amostra.</span><span class="sxs-lookup"><span data-stu-id="079ab-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="079ab-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="079ab-111">See also</span></span>

- [<span data-ttu-id="079ab-112">Animar traduções 3D</span><span class="sxs-lookup"><span data-stu-id="079ab-112">Animate 3D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="079ab-113">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="079ab-113">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="079ab-114">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="079ab-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
