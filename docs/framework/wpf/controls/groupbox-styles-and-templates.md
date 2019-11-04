---
title: Estilos e modelos GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 0835c106ffbda86bca8e01bc61adebfc1ab0c2cb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459643"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="8b601-102">Estilos e modelos GroupBox</span><span class="sxs-lookup"><span data-stu-id="8b601-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="8b601-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="8b601-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="8b601-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="8b601-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8b601-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="8b601-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="8b601-106">Partes da caixa de GroupBox</span><span class="sxs-lookup"><span data-stu-id="8b601-106">GroupBox Parts</span></span>  
 <span data-ttu-id="8b601-107">O controle de <xref:System.Windows.Controls.GroupBox> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="8b601-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="8b601-108">Estados da GroupBox</span><span class="sxs-lookup"><span data-stu-id="8b601-108">GroupBox States</span></span>  
 <span data-ttu-id="8b601-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="8b601-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="8b601-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="8b601-110">VisualState Name</span></span>|<span data-ttu-id="8b601-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="8b601-111">VisualStateGroup Name</span></span>|<span data-ttu-id="8b601-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b601-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8b601-113">Válido</span><span class="sxs-lookup"><span data-stu-id="8b601-113">Valid</span></span>|<span data-ttu-id="8b601-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8b601-114">ValidationStates</span></span>|<span data-ttu-id="8b601-115">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="8b601-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8b601-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8b601-116">InvalidFocused</span></span>|<span data-ttu-id="8b601-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8b601-117">ValidationStates</span></span>|<span data-ttu-id="8b601-118">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="8b601-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8b601-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8b601-119">InvalidUnfocused</span></span>|<span data-ttu-id="8b601-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8b601-120">ValidationStates</span></span>|<span data-ttu-id="8b601-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="8b601-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="8b601-122">Exemplo de ControlTemplate de GroupBox</span><span class="sxs-lookup"><span data-stu-id="8b601-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="8b601-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="8b601-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="8b601-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b601-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8b601-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="8b601-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b601-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b601-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8b601-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="8b601-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="8b601-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="8b601-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="8b601-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="8b601-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="8b601-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8b601-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
