---
title: Estilos e modelos ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: f30a0abb3e4252737e513b531b8d5f49a0d47f0b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458452"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="2e47d-102">Estilos e modelos ScrollBar</span><span class="sxs-lookup"><span data-stu-id="2e47d-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="2e47d-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="2e47d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="2e47d-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="2e47d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2e47d-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2e47d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="2e47d-106">Partes da barra de rolagem</span><span class="sxs-lookup"><span data-stu-id="2e47d-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="2e47d-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="2e47d-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="2e47d-108">Parte</span><span class="sxs-lookup"><span data-stu-id="2e47d-108">Part</span></span>|<span data-ttu-id="2e47d-109">Digite</span><span class="sxs-lookup"><span data-stu-id="2e47d-109">Type</span></span>|<span data-ttu-id="2e47d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e47d-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2e47d-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="2e47d-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="2e47d-112">O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="2e47d-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="2e47d-113">Estados da barra de rolagem</span><span class="sxs-lookup"><span data-stu-id="2e47d-113">ScrollBar States</span></span>  
 <span data-ttu-id="2e47d-114">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="2e47d-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="2e47d-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="2e47d-115">VisualState Name</span></span>|<span data-ttu-id="2e47d-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2e47d-116">VisualStateGroup Name</span></span>|<span data-ttu-id="2e47d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e47d-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="2e47d-118">Normal</span><span class="sxs-lookup"><span data-stu-id="2e47d-118">Normal</span></span>|<span data-ttu-id="2e47d-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2e47d-119">CommonStates</span></span>|<span data-ttu-id="2e47d-120">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="2e47d-120">The default state.</span></span>|  
|<span data-ttu-id="2e47d-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="2e47d-121">MouseOver</span></span>|<span data-ttu-id="2e47d-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2e47d-122">CommonStates</span></span>|<span data-ttu-id="2e47d-123">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="2e47d-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="2e47d-124">Disabled</span><span class="sxs-lookup"><span data-stu-id="2e47d-124">Disabled</span></span>|<span data-ttu-id="2e47d-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2e47d-125">CommonStates</span></span>|<span data-ttu-id="2e47d-126">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="2e47d-126">The control is disabled.</span></span>|  
|<span data-ttu-id="2e47d-127">Válido</span><span class="sxs-lookup"><span data-stu-id="2e47d-127">Valid</span></span>|<span data-ttu-id="2e47d-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2e47d-128">ValidationStates</span></span>|<span data-ttu-id="2e47d-129">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="2e47d-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2e47d-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2e47d-130">InvalidFocused</span></span>|<span data-ttu-id="2e47d-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2e47d-131">ValidationStates</span></span>|<span data-ttu-id="2e47d-132">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="2e47d-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="2e47d-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2e47d-133">InvalidUnfocused</span></span>|<span data-ttu-id="2e47d-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2e47d-134">ValidationStates</span></span>|<span data-ttu-id="2e47d-135">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="2e47d-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="2e47d-136">Exemplo de ControlTemplate de ScrollBar</span><span class="sxs-lookup"><span data-stu-id="2e47d-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="2e47d-137">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="2e47d-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="2e47d-138">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="2e47d-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2e47d-139">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2e47d-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e47d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e47d-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2e47d-141">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="2e47d-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2e47d-142">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="2e47d-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2e47d-143">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="2e47d-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2e47d-144">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2e47d-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
