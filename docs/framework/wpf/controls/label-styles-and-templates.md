---
title: Estilos e modelos de rótulo
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: d2bb348fc9c0348fd8093452e022df7ab4e0b3f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137079"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="fa9f6-102">Estilos e modelos de rótulo</span><span class="sxs-lookup"><span data-stu-id="fa9f6-102">Label Styles and Templates</span></span>
<span data-ttu-id="fa9f6-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="fa9f6-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fa9f6-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="fa9f6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="fa9f6-106">Partes de rótulo</span><span class="sxs-lookup"><span data-stu-id="fa9f6-106">Label Parts</span></span>  
 <span data-ttu-id="fa9f6-107">O <xref:System.Windows.Controls.Label> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="fa9f6-108">Estados de rótulo</span><span class="sxs-lookup"><span data-stu-id="fa9f6-108">Label States</span></span>  
 <span data-ttu-id="fa9f6-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="fa9f6-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="fa9f6-110">VisualState Name</span></span>|<span data-ttu-id="fa9f6-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fa9f6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="fa9f6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa9f6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fa9f6-113">Válido</span><span class="sxs-lookup"><span data-stu-id="fa9f6-113">Valid</span></span>|<span data-ttu-id="fa9f6-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fa9f6-114">ValidationStates</span></span>|<span data-ttu-id="fa9f6-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fa9f6-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fa9f6-116">InvalidFocused</span></span>|<span data-ttu-id="fa9f6-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fa9f6-117">ValidationStates</span></span>|<span data-ttu-id="fa9f6-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fa9f6-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fa9f6-119">InvalidUnfocused</span></span>|<span data-ttu-id="fa9f6-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fa9f6-120">ValidationStates</span></span>|<span data-ttu-id="fa9f6-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="fa9f6-122">Exemplo de ControlTemplate de rótulo</span><span class="sxs-lookup"><span data-stu-id="fa9f6-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="fa9f6-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="fa9f6-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="fa9f6-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fa9f6-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="fa9f6-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9f6-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa9f6-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fa9f6-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="fa9f6-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fa9f6-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="fa9f6-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fa9f6-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="fa9f6-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="fa9f6-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="fa9f6-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
