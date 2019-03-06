---
title: Estilos e modelos de janela
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: 416202f22fcdad1d98f28889af6bdcdf5671587c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376293"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="21a6c-102">Estilos e modelos de janela</span><span class="sxs-lookup"><span data-stu-id="21a6c-102">Window Styles and Templates</span></span>
<span data-ttu-id="21a6c-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Window> controle.</span><span class="sxs-lookup"><span data-stu-id="21a6c-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="21a6c-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="21a6c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="21a6c-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="21a6c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="21a6c-106">Partes da janela</span><span class="sxs-lookup"><span data-stu-id="21a6c-106">Window Parts</span></span>  
 <span data-ttu-id="21a6c-107">O <xref:System.Windows.Window> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="21a6c-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="21a6c-108">Estados de janela</span><span class="sxs-lookup"><span data-stu-id="21a6c-108">Window States</span></span>  
 <span data-ttu-id="21a6c-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Window> controle.</span><span class="sxs-lookup"><span data-stu-id="21a6c-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="21a6c-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="21a6c-110">VisualState Name</span></span>|<span data-ttu-id="21a6c-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="21a6c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="21a6c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="21a6c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="21a6c-113">Válido</span><span class="sxs-lookup"><span data-stu-id="21a6c-113">Valid</span></span>|<span data-ttu-id="21a6c-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21a6c-114">ValidationStates</span></span>|<span data-ttu-id="21a6c-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="21a6c-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="21a6c-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="21a6c-116">InvalidFocused</span></span>|<span data-ttu-id="21a6c-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21a6c-117">ValidationStates</span></span>|<span data-ttu-id="21a6c-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="21a6c-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="21a6c-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="21a6c-119">InvalidUnfocused</span></span>|<span data-ttu-id="21a6c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21a6c-120">ValidationStates</span></span>|<span data-ttu-id="21a6c-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="21a6c-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="21a6c-122">Exemplo de ControlTemplate de janela</span><span class="sxs-lookup"><span data-stu-id="21a6c-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="21a6c-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Window> controle.</span><span class="sxs-lookup"><span data-stu-id="21a6c-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="21a6c-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="21a6c-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="21a6c-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="21a6c-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a6c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21a6c-126">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="21a6c-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="21a6c-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="21a6c-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="21a6c-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="21a6c-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="21a6c-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="21a6c-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21a6c-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
