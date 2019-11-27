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
ms.openlocfilehash: 7093a78555aefd73f9bb05c0a7b5fab6b66176fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283411"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="f3b5e-102">Estilos e modelos ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f3b5e-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="f3b5e-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="f3b5e-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f3b5e-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="f3b5e-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="f3b5e-106">Partes da barra de rolagem</span><span class="sxs-lookup"><span data-stu-id="f3b5e-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="f3b5e-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f3b5e-108">Parte</span><span class="sxs-lookup"><span data-stu-id="f3b5e-108">Part</span></span>|<span data-ttu-id="f3b5e-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="f3b5e-109">Type</span></span>|<span data-ttu-id="f3b5e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3b5e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f3b5e-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f3b5e-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f3b5e-112">O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="f3b5e-113">Estados da barra de rolagem</span><span class="sxs-lookup"><span data-stu-id="f3b5e-113">ScrollBar States</span></span>  
 <span data-ttu-id="f3b5e-114">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f3b5e-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="f3b5e-115">VisualState Name</span></span>|<span data-ttu-id="f3b5e-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f3b5e-116">VisualStateGroup Name</span></span>|<span data-ttu-id="f3b5e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3b5e-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f3b5e-118">Normal</span><span class="sxs-lookup"><span data-stu-id="f3b5e-118">Normal</span></span>|<span data-ttu-id="f3b5e-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3b5e-119">CommonStates</span></span>|<span data-ttu-id="f3b5e-120">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-120">The default state.</span></span>|  
|<span data-ttu-id="f3b5e-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f3b5e-121">MouseOver</span></span>|<span data-ttu-id="f3b5e-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3b5e-122">CommonStates</span></span>|<span data-ttu-id="f3b5e-123">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f3b5e-124">Desabilitado</span><span class="sxs-lookup"><span data-stu-id="f3b5e-124">Disabled</span></span>|<span data-ttu-id="f3b5e-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3b5e-125">CommonStates</span></span>|<span data-ttu-id="f3b5e-126">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-126">The control is disabled.</span></span>|  
|<span data-ttu-id="f3b5e-127">Válido</span><span class="sxs-lookup"><span data-stu-id="f3b5e-127">Valid</span></span>|<span data-ttu-id="f3b5e-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3b5e-128">ValidationStates</span></span>|<span data-ttu-id="f3b5e-129">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f3b5e-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f3b5e-130">InvalidFocused</span></span>|<span data-ttu-id="f3b5e-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3b5e-131">ValidationStates</span></span>|<span data-ttu-id="f3b5e-132">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="f3b5e-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f3b5e-133">InvalidUnfocused</span></span>|<span data-ttu-id="f3b5e-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3b5e-134">ValidationStates</span></span>|<span data-ttu-id="f3b5e-135">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="f3b5e-136">Exemplo de ControlTemplate de ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f3b5e-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="f3b5e-137">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="f3b5e-138">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="f3b5e-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f3b5e-139">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f3b5e-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b5e-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3b5e-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f3b5e-141">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="f3b5e-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f3b5e-142">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="f3b5e-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f3b5e-143">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f3b5e-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f3b5e-144">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="f3b5e-144">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
