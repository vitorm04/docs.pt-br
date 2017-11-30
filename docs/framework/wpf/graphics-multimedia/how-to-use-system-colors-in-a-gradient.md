---
title: Como usar cores do sistema em um gradiente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="c322e-102">Como usar cores do sistema em um gradiente</span><span class="sxs-lookup"><span data-stu-id="c322e-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="c322e-103">Para usar uma cor do sistema em um gradiente, você deve usar o  *\<SystemColor >*cor e  *\<SystemColor >*ColorKey a propriedades estáticas do <xref:System.Windows.SystemColors> classe para obter um referência para a cor, onde  *\<SystemColor >* é o nome da cor do sistema desejada.</span><span class="sxs-lookup"><span data-stu-id="c322e-103">To use a system color in a gradient, you use the *\<SystemColor>*Color and *\<SystemColor>*ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="c322e-104">Use o  *\<SystemColor >*ColorKey propriedades quando você deseja criar uma referência dinâmica que se atualiza automaticamente com as alterações de tema do sistema.</span><span class="sxs-lookup"><span data-stu-id="c322e-104">Use the *\<SystemColor>*ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="c322e-105">Caso contrário, use o  *\<SystemColor >*propriedades de cores.</span><span class="sxs-lookup"><span data-stu-id="c322e-105">Otherwise, use the *\<SystemColor>*Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c322e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c322e-106">Example</span></span>  
 <span data-ttu-id="c322e-107">O exemplo a seguir usa recursos de cores de sistema dinâmico para criar um gradiente.</span><span class="sxs-lookup"><span data-stu-id="c322e-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="c322e-108">O exemplo a seguir usa recursos de cores do sistema estático para criar um gradiente.</span><span class="sxs-lookup"><span data-stu-id="c322e-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c322e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c322e-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="c322e-110">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="c322e-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="c322e-111">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="c322e-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
