---
title: 'Como: Pintar uma área com um gradiente radial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921818"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="1c3db-102">Como: Pintar uma área com um gradiente radial</span><span class="sxs-lookup"><span data-stu-id="1c3db-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="1c3db-103">Este exemplo mostra como usar o <xref:System.Windows.Media.RadialGradientBrush> classe pintar uma área com um gradiente radial.</span><span class="sxs-lookup"><span data-stu-id="1c3db-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c3db-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c3db-104">Example</span></span>  
 <span data-ttu-id="1c3db-105">O exemplo a seguir usa um <xref:System.Windows.Media.RadialGradientBrush> para pintar um retângulo com um gradiente radial que faz a transição de amarelo para vermelho para azul para verde limão.</span><span class="sxs-lookup"><span data-stu-id="1c3db-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="1c3db-106">A ilustração a seguir mostra o gradiente do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1c3db-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="1c3db-107">Do gradiente foram realçado.</span><span class="sxs-lookup"><span data-stu-id="1c3db-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="1c3db-108">![Marcas de gradiente em um gradiente radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="1c3db-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c3db-109">Os exemplos neste tópico usam o sistema de coordenadas padrão para definir pontos de controle.</span><span class="sxs-lookup"><span data-stu-id="1c3db-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="1c3db-110">O sistema de coordenadas padrão é relativo a uma caixa delimitadora: 0 indica 0% da caixa delimitadora e 1 indica 100 por cento da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="1c3db-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="1c3db-111">Você pode alterar esse sistema de coordenadas definindo a <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriedade para o valor <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="1c3db-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="1c3db-112">Um sistema de coordenadas absoluto não é relativo a uma caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="1c3db-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="1c3db-113">Os valores são interpretados diretamente no espaço local.</span><span class="sxs-lookup"><span data-stu-id="1c3db-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="1c3db-114">Para adicionais <xref:System.Windows.Media.RadialGradientBrush> exemplos, consulte a [exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="1c3db-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="1c3db-115">Para obter mais informações sobre gradientes e outros tipos de pincéis, veja [Visão geral de pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c3db-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
