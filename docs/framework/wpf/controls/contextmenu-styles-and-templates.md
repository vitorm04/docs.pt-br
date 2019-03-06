---
title: Estilos e modelos ContextMenu
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: be26156d74f3a3509bf150e5611512172f08a14e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369062"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="d893e-102">Estilos e modelos ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d893e-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="d893e-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ContextMenu> controle.</span><span class="sxs-lookup"><span data-stu-id="d893e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="d893e-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="d893e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d893e-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d893e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="d893e-106">Partes de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d893e-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="d893e-107">O <xref:System.Windows.Controls.ContextMenu> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="d893e-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="d893e-108">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ContextMenu>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="d893e-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="d893e-109">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item em de <xref:System.Windows.Controls.ContextMenu>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem no controle).</span><span class="sxs-lookup"><span data-stu-id="d893e-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="d893e-110">Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve dar a <xref:System.Windows.Controls.ItemsPresenter> o nome, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="d893e-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="d893e-111">Estados de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d893e-111">ContextMenu States</span></span>  
 <span data-ttu-id="d893e-112">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ContextMenu> controle.</span><span class="sxs-lookup"><span data-stu-id="d893e-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="d893e-113">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="d893e-113">VisualState Name</span></span>|<span data-ttu-id="d893e-114">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d893e-114">VisualStateGroup Name</span></span>|<span data-ttu-id="d893e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d893e-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d893e-116">Válido</span><span class="sxs-lookup"><span data-stu-id="d893e-116">Valid</span></span>|<span data-ttu-id="d893e-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d893e-117">ValidationStates</span></span>|<span data-ttu-id="d893e-118">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="d893e-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d893e-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d893e-119">InvalidFocused</span></span>|<span data-ttu-id="d893e-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d893e-120">ValidationStates</span></span>|<span data-ttu-id="d893e-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="d893e-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d893e-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d893e-122">InvalidUnfocused</span></span>|<span data-ttu-id="d893e-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d893e-123">ValidationStates</span></span>|<span data-ttu-id="d893e-124">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="d893e-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="d893e-125">Exemplo de ControlTemplate de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d893e-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="d893e-126">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ContextMenu> controle.</span><span class="sxs-lookup"><span data-stu-id="d893e-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="d893e-127">O <xref:System.Windows.Controls.ControlTemplate> usa os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="d893e-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d893e-128">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d893e-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d893e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d893e-129">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d893e-130">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="d893e-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d893e-131">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="d893e-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d893e-132">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="d893e-132">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d893e-133">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d893e-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
