---
title: 'Como: Pintar uma área com um pincel de sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: e713903e2cfbb63cb64ceb94621317f9e76dea70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195040"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="9bd39-102">Como: Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="9bd39-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="9bd39-103">O <xref:System.Windows.SystemColors> classe fornece acesso a pincéis do sistema e cores, como <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, e <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bd39-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="9bd39-104">Um pincel de sistema é um <xref:System.Windows.Media.SolidColorBrush> objeto que pinta uma área com a cor especificada do sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd39-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="9bd39-105">Um pincel do sistema sempre produz um preenchimento sólido; ele não pode ser usado para criar um gradiente.</span><span class="sxs-lookup"><span data-stu-id="9bd39-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="9bd39-106">Você pode usar pincéis do sistema como um recurso dinâmico ou estático.</span><span class="sxs-lookup"><span data-stu-id="9bd39-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="9bd39-107">Use um recurso dinâmico se desejar que o pincel seja atualizado automaticamente se o usuário alterar o pincel do sistema enquanto o aplicativo está em execução; caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="9bd39-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="9bd39-108">A classe SystemColors contém uma variedade de propriedades estáticas que seguem uma convenção de nomenclatura estrita:</span><span class="sxs-lookup"><span data-stu-id="9bd39-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="9bd39-109">*\<SystemColor>* Pincel</span><span class="sxs-lookup"><span data-stu-id="9bd39-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="9bd39-110">Obtém uma referência estática a uma <xref:System.Windows.Media.SolidColorBrush> da cor especificada do sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd39-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="9bd39-111">*\<SystemColor>* BrushKey</span><span class="sxs-lookup"><span data-stu-id="9bd39-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="9bd39-112">Obtém uma referência dinâmica a um <xref:System.Windows.Media.SolidColorBrush> da cor especificada do sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd39-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="9bd39-113">*\<SystemColor>* Cor</span><span class="sxs-lookup"><span data-stu-id="9bd39-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="9bd39-114">Obtém uma referência estática a uma <xref:System.Windows.Media.Color> estrutura de cor especificada do sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd39-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="9bd39-115">*\<SystemColor>* ColorKey</span><span class="sxs-lookup"><span data-stu-id="9bd39-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="9bd39-116">Obtém uma referência dinâmica para o <xref:System.Windows.Media.Color> estrutura de cor especificada do sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd39-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="9bd39-117">Uma cor do sistema é um <xref:System.Windows.Media.Color> estrutura que pode ser usada para configurar um pincel.</span><span class="sxs-lookup"><span data-stu-id="9bd39-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="9bd39-118">Por exemplo, você pode criar um gradiente usando cores do sistema definindo a <xref:System.Windows.Media.GradientStop.Color%2A> propriedades de um <xref:System.Windows.Media.LinearGradientBrush> paradas de gradiente do objeto com as cores do sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd39-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="9bd39-119">Por exemplo, consulte [usar cores do sistema em um gradiente](how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="9bd39-119">For an example, see [Use System Colors in a Gradient](how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd39-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd39-120">Example</span></span>  
 <span data-ttu-id="9bd39-121">O exemplo a seguir usa uma referência de pincel de sistema dinâmico para definir a tela de fundo de um botão.</span><span class="sxs-lookup"><span data-stu-id="9bd39-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="9bd39-122">O exemplo a seguir usa uma referência de pincel de sistema estático para definir a tela de fundo de um botão.</span><span class="sxs-lookup"><span data-stu-id="9bd39-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="9bd39-123">Para obter um exemplo que mostra como usar uma cor do sistema em um gradiente, consulte [usar cores do sistema em um gradiente](how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="9bd39-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd39-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd39-124">See also</span></span>

- [<span data-ttu-id="9bd39-125">Usar cores do sistema em um gradiente</span><span class="sxs-lookup"><span data-stu-id="9bd39-125">Use System Colors in a Gradient</span></span>](how-to-use-system-colors-in-a-gradient.md)
- [<span data-ttu-id="9bd39-126">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="9bd39-126">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
