---
title: 'Como: Criar uma forma usando um StreamGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: ce2097568349ad376540163f5fe05d6a3e5b0643
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348024"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="a03b3-102">Como: Criar uma forma usando um StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="a03b3-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="a03b3-103"><xref:System.Windows.Media.StreamGeometry> é uma alternativa leve para <xref:System.Windows.Media.PathGeometry> para criar formas geométricas.</span><span class="sxs-lookup"><span data-stu-id="a03b3-103"><xref:System.Windows.Media.StreamGeometry> is lightweight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="a03b3-104">Use um <xref:System.Windows.Media.StreamGeometry> quando precisar descrever uma geometria complexa mas não deseja que a sobrecarga de dar suporte a vinculação de dados, animação ou modificação.</span><span class="sxs-lookup"><span data-stu-id="a03b3-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="a03b3-105">Por exemplo, devido à sua eficiência, a <xref:System.Windows.Media.StreamGeometry> classe é uma boa opção para descrever adornos.</span><span class="sxs-lookup"><span data-stu-id="a03b3-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a03b3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a03b3-106">Example</span></span>  
 <span data-ttu-id="a03b3-107">O exemplo a seguir usa a sintaxe de atributo para criar um triangular <xref:System.Windows.Media.StreamGeometry> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a03b3-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="a03b3-108">Para obter mais informações sobre <xref:System.Windows.Media.StreamGeometry> sintaxe de atributo, consulte a [sintaxe de marcação de caminho](path-markup-syntax.md) página.</span><span class="sxs-lookup"><span data-stu-id="a03b3-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a03b3-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a03b3-109">Example</span></span>  
 <span data-ttu-id="a03b3-110">O próximo exemplo usa um <xref:System.Windows.Media.StreamGeometry> para definir um triângulo no código.</span><span class="sxs-lookup"><span data-stu-id="a03b3-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="a03b3-111">Primeiro, o exemplo cria um <xref:System.Windows.Media.StreamGeometry>, em seguida, obtém um <xref:System.Windows.Media.StreamGeometryContext> e o utiliza para descrever o triângulo.</span><span class="sxs-lookup"><span data-stu-id="a03b3-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="a03b3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a03b3-112">Example</span></span>  
 <span data-ttu-id="a03b3-113">O exemplo a seguir cria um método que usa um <xref:System.Windows.Media.StreamGeometry> e <xref:System.Windows.Media.StreamGeometryContext> para definir uma forma geométrica com base em parâmetros especificados.</span><span class="sxs-lookup"><span data-stu-id="a03b3-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a03b3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a03b3-114">See also</span></span>

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [<span data-ttu-id="a03b3-115">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="a03b3-115">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [<span data-ttu-id="a03b3-116">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="a03b3-116">Geometry Overview</span></span>](geometry-overview.md)
