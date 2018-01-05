---
title: "Como pintar uma área com um pincel de sistema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87979c16d52262c665e2fb37fdf6d7550c5930c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="3028f-102">Como pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="3028f-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="3028f-103">O <xref:System.Windows.SystemColors> classe fornece acesso a sistema pincéis e cores, como <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, e <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="3028f-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="3028f-104">Um pincel de sistema é um <xref:System.Windows.Media.SolidColorBrush> objeto que pinta uma área com a cor de sistema especificado.</span><span class="sxs-lookup"><span data-stu-id="3028f-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="3028f-105">Um pincel do sistema sempre produz um preenchimento sólido; ele não pode ser usado para criar um gradiente.</span><span class="sxs-lookup"><span data-stu-id="3028f-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="3028f-106">Você pode usar pincéis do sistema como um recurso dinâmico ou estático.</span><span class="sxs-lookup"><span data-stu-id="3028f-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="3028f-107">Use um recurso dinâmico se desejar que o pincel seja atualizado automaticamente se o usuário alterar o pincel do sistema enquanto o aplicativo está em execução; caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="3028f-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="3028f-108">A classe SystemColors contém uma variedade de propriedades estáticas que seguem uma convenção de nomenclatura estrita:</span><span class="sxs-lookup"><span data-stu-id="3028f-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="3028f-109">*\<SystemColor>*Pincel</span><span class="sxs-lookup"><span data-stu-id="3028f-109">*\<SystemColor>*Brush</span></span>  
  
     <span data-ttu-id="3028f-110">Obtém uma referência estática a uma <xref:System.Windows.Media.SolidColorBrush> de cor do sistema especificada.</span><span class="sxs-lookup"><span data-stu-id="3028f-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="3028f-111">*\<SystemColor>*BrushKey</span><span class="sxs-lookup"><span data-stu-id="3028f-111">*\<SystemColor>*BrushKey</span></span>  
  
     <span data-ttu-id="3028f-112">Obtém uma referência dinâmica para um <xref:System.Windows.Media.SolidColorBrush> de cor do sistema especificada.</span><span class="sxs-lookup"><span data-stu-id="3028f-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="3028f-113">*\<SystemColor>*Cor</span><span class="sxs-lookup"><span data-stu-id="3028f-113">*\<SystemColor>*Color</span></span>  
  
     <span data-ttu-id="3028f-114">Obtém uma referência estática a uma <xref:System.Windows.Media.Color> estrutura de cor do sistema especificada.</span><span class="sxs-lookup"><span data-stu-id="3028f-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="3028f-115">*\<SystemColor>*ColorKey</span><span class="sxs-lookup"><span data-stu-id="3028f-115">*\<SystemColor>*ColorKey</span></span>  
  
     <span data-ttu-id="3028f-116">Obtém uma referência dinâmica para o <xref:System.Windows.Media.Color> estrutura de cor do sistema especificada.</span><span class="sxs-lookup"><span data-stu-id="3028f-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="3028f-117">Uma cor do sistema é um <xref:System.Windows.Media.Color> estrutura que pode ser usada para configurar um pincel.</span><span class="sxs-lookup"><span data-stu-id="3028f-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="3028f-118">Por exemplo, você pode criar um gradiente usando cores do sistema definindo o <xref:System.Windows.Media.GradientStop.Color%2A> propriedades de um <xref:System.Windows.Media.LinearGradientBrush> paradas de gradiente do objeto com cores do sistema.</span><span class="sxs-lookup"><span data-stu-id="3028f-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="3028f-119">Para obter um exemplo, consulte [usar cores do sistema em um gradiente](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="3028f-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3028f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3028f-120">Example</span></span>  
 <span data-ttu-id="3028f-121">O exemplo a seguir usa uma referência de pincel de sistema dinâmico para definir a tela de fundo de um botão.</span><span class="sxs-lookup"><span data-stu-id="3028f-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="3028f-122">O exemplo a seguir usa uma referência de pincel de sistema estático para definir a tela de fundo de um botão.</span><span class="sxs-lookup"><span data-stu-id="3028f-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="3028f-123">Para obter um exemplo mostrando como usar uma cor do sistema em um gradiente, consulte [usar cores do sistema em um gradiente](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="3028f-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3028f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3028f-124">See Also</span></span>  
 [<span data-ttu-id="3028f-125">Usar cores do sistema em um gradiente</span><span class="sxs-lookup"><span data-stu-id="3028f-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="3028f-126">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="3028f-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
