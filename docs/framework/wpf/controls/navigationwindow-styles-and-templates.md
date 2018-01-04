---
title: Estilos e modelos NavigationWindow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b638d43fb59506572e2ccddd9da7188639bff279
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="e752f-102">Estilos e modelos NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="e752f-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="e752f-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Navigation.NavigationWindow> controle.</span><span class="sxs-lookup"><span data-stu-id="e752f-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="e752f-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="e752f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e752f-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e752f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="e752f-106">NavigationWindow partes</span><span class="sxs-lookup"><span data-stu-id="e752f-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="e752f-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Navigation.NavigationWindow> controle.</span><span class="sxs-lookup"><span data-stu-id="e752f-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="e752f-108">Parte</span><span class="sxs-lookup"><span data-stu-id="e752f-108">Part</span></span>|<span data-ttu-id="e752f-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="e752f-109">Type</span></span>|<span data-ttu-id="e752f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e752f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e752f-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="e752f-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="e752f-112">A área do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e752f-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="e752f-113">NavigationWindow Estados</span><span class="sxs-lookup"><span data-stu-id="e752f-113">NavigationWindow States</span></span>  
 <span data-ttu-id="e752f-114">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Navigation.NavigationWindow> controle.</span><span class="sxs-lookup"><span data-stu-id="e752f-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="e752f-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="e752f-115">VisualState Name</span></span>|<span data-ttu-id="e752f-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e752f-116">VisualStateGroup Name</span></span>|<span data-ttu-id="e752f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="e752f-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e752f-118">Válido</span><span class="sxs-lookup"><span data-stu-id="e752f-118">Valid</span></span>|<span data-ttu-id="e752f-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e752f-119">ValidationStates</span></span>|<span data-ttu-id="e752f-120">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="e752f-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e752f-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e752f-121">InvalidFocused</span></span>|<span data-ttu-id="e752f-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e752f-122">ValidationStates</span></span>|<span data-ttu-id="e752f-123">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="e752f-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e752f-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e752f-124">InvalidUnfocused</span></span>|<span data-ttu-id="e752f-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e752f-125">ValidationStates</span></span>|<span data-ttu-id="e752f-126">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="e752f-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="e752f-127">Exemplo de ControlTemplate NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="e752f-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="e752f-128">Embora esse exemplo contém todos os elementos que são definidos no <xref:System.Windows.Controls.ControlTemplate> de um <xref:System.Windows.Navigation.NavigationWindow> por padrão, os valores específicos devem ser considerados como exemplos.</span><span class="sxs-lookup"><span data-stu-id="e752f-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="e752f-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="e752f-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e752f-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="e752f-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e752f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e752f-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e752f-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="e752f-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e752f-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="e752f-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e752f-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="e752f-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e752f-135">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e752f-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
