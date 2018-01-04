---
title: Estilos e modelos GroupBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99150de10fcbd45d3617621a916793ad5cfe72db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="ed992-102">Estilos e modelos GroupBox</span><span class="sxs-lookup"><span data-stu-id="ed992-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="ed992-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="ed992-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="ed992-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="ed992-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ed992-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ed992-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="ed992-106">Partes de grupo</span><span class="sxs-lookup"><span data-stu-id="ed992-106">GroupBox Parts</span></span>  
 <span data-ttu-id="ed992-107">O <xref:System.Windows.Controls.GroupBox> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="ed992-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="ed992-108">Estados de grupo</span><span class="sxs-lookup"><span data-stu-id="ed992-108">GroupBox States</span></span>  
 <span data-ttu-id="ed992-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="ed992-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="ed992-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="ed992-110">VisualState Name</span></span>|<span data-ttu-id="ed992-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ed992-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ed992-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed992-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ed992-113">Válido</span><span class="sxs-lookup"><span data-stu-id="ed992-113">Valid</span></span>|<span data-ttu-id="ed992-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed992-114">ValidationStates</span></span>|<span data-ttu-id="ed992-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="ed992-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ed992-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ed992-116">InvalidFocused</span></span>|<span data-ttu-id="ed992-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed992-117">ValidationStates</span></span>|<span data-ttu-id="ed992-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="ed992-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ed992-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ed992-119">InvalidUnfocused</span></span>|<span data-ttu-id="ed992-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed992-120">ValidationStates</span></span>|<span data-ttu-id="ed992-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="ed992-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="ed992-122">Exemplo de ControlTemplate de GroupBox</span><span class="sxs-lookup"><span data-stu-id="ed992-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ed992-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="ed992-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="ed992-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="ed992-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ed992-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="ed992-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed992-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed992-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ed992-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="ed992-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ed992-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="ed992-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ed992-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="ed992-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ed992-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ed992-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
