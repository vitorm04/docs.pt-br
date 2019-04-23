---
title: 'Como: Usar cores do sistema em um gradiente'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229434"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="bc345-102">Como: Usar cores do sistema em um gradiente</span><span class="sxs-lookup"><span data-stu-id="bc345-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="bc345-103">Para usar uma cor do sistema em um gradiente, você deve usar o  *\<SystemColor >* cor e  *\<SystemColor >* ColorKey a propriedades estáticas do <xref:System.Windows.SystemColors> classe para obter uma referência para a cor, onde  *\<SystemColor >* é o nome da cor do sistema desejado.</span><span class="sxs-lookup"><span data-stu-id="bc345-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="bc345-104">Use o  *\<SystemColor >* ColorKey propriedades quando você deseja criar uma referência dinâmica que se atualiza automaticamente com as alterações de tema do sistema.</span><span class="sxs-lookup"><span data-stu-id="bc345-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="bc345-105">Caso contrário, use o  *\<SystemColor >* propriedades de cor.</span><span class="sxs-lookup"><span data-stu-id="bc345-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc345-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc345-106">Example</span></span>  
 <span data-ttu-id="bc345-107">O exemplo a seguir usa recursos de cor do sistema dinâmico para criar um gradiente.</span><span class="sxs-lookup"><span data-stu-id="bc345-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="bc345-108">O exemplo a seguir usa recursos de cor do sistema estático para criar um gradiente.</span><span class="sxs-lookup"><span data-stu-id="bc345-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bc345-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc345-109">See also</span></span>

- <xref:System.Windows.SystemColors>
- [<span data-ttu-id="bc345-110">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="bc345-110">Paint an Area with a System Brush</span></span>](how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="bc345-111">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="bc345-111">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
