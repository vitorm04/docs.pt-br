---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: d83713a81e7675a68482890c2401f1a0a6803abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914228"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="a367e-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="a367e-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="a367e-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a367e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a367e-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a367e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a367e-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o suporte para controles padrão em aplicativos desenvolvidos para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]as [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]estruturas do [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] , e.</span><span class="sxs-lookup"><span data-stu-id="a367e-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="a367e-106">Controles de Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a367e-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="a367e-107">Todos [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] os elementos de controle que fornecem informações ou suporte para interação do usuário têm suporte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nativo completo para o.</span><span class="sxs-lookup"><span data-stu-id="a367e-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a367e-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a367e-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="a367e-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="a367e-109">Win32 Controls</span></span>  
 <span data-ttu-id="a367e-110">A [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] maioria dos controles é [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] exposta a provedores do lado do cliente em UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="a367e-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a367e-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a367e-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a367e-112">O suporte completo é fornecido somente para controles da versão 6 do ComCtrl32. dll (disponível [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] com e posterior).</span><span class="sxs-lookup"><span data-stu-id="a367e-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="a367e-113">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="a367e-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a367e-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="a367e-114">Class name</span></span>|<span data-ttu-id="a367e-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="a367e-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a367e-116">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-116">Button</span></span>|<span data-ttu-id="a367e-117">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-117">Button</span></span>|  
|<span data-ttu-id="a367e-118">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-118">Button</span></span>|<span data-ttu-id="a367e-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a367e-119">RadioButton</span></span>|  
|<span data-ttu-id="a367e-120">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-120">Button</span></span>|<span data-ttu-id="a367e-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="a367e-121">Group</span></span>|  
|<span data-ttu-id="a367e-122">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-122">Button</span></span>|<span data-ttu-id="a367e-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a367e-123">CheckBox</span></span>|  
|<span data-ttu-id="a367e-124">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-124">Button</span></span>|<span data-ttu-id="a367e-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="a367e-125">Hyperlink</span></span>|  
|<span data-ttu-id="a367e-126">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-126">Button</span></span>|<span data-ttu-id="a367e-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="a367e-127">SplitButton</span></span>|  
|<span data-ttu-id="a367e-128">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-128">Button</span></span>|<span data-ttu-id="a367e-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a367e-129">CheckBox</span></span>|  
|<span data-ttu-id="a367e-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="a367e-130">ComboBoxEx32</span></span>|<span data-ttu-id="a367e-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a367e-131">ComboBox</span></span>|  
|<span data-ttu-id="a367e-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a367e-132">ComboBox</span></span>|<span data-ttu-id="a367e-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a367e-133">ComboBox</span></span>|  
|<span data-ttu-id="a367e-134">Editar</span><span class="sxs-lookup"><span data-stu-id="a367e-134">Edit</span></span>|<span data-ttu-id="a367e-135">Documento</span><span class="sxs-lookup"><span data-stu-id="a367e-135">Document</span></span>|  
|<span data-ttu-id="a367e-136">Editar</span><span class="sxs-lookup"><span data-stu-id="a367e-136">Edit</span></span>|<span data-ttu-id="a367e-137">Editar</span><span class="sxs-lookup"><span data-stu-id="a367e-137">Edit</span></span>|  
|<span data-ttu-id="a367e-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="a367e-138">SysLink</span></span>|<span data-ttu-id="a367e-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="a367e-139">Hyperlink</span></span>|  
|<span data-ttu-id="a367e-140">Estático</span><span class="sxs-lookup"><span data-stu-id="a367e-140">Static</span></span>|<span data-ttu-id="a367e-141">Texto</span><span class="sxs-lookup"><span data-stu-id="a367e-141">Text</span></span>|  
|<span data-ttu-id="a367e-142">Estático</span><span class="sxs-lookup"><span data-stu-id="a367e-142">Static</span></span>|<span data-ttu-id="a367e-143">Image</span><span class="sxs-lookup"><span data-stu-id="a367e-143">Image</span></span>|  
|<span data-ttu-id="a367e-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="a367e-144">SysIPAddress32</span></span>|<span data-ttu-id="a367e-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="a367e-145">Custom</span></span>|  
|<span data-ttu-id="a367e-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="a367e-146">SysHeader32</span></span>|<span data-ttu-id="a367e-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="a367e-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="a367e-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a367e-148">SysListView32</span></span>|<span data-ttu-id="a367e-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a367e-149">DataGrid</span></span>|  
|<span data-ttu-id="a367e-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a367e-150">SysListView32</span></span>|<span data-ttu-id="a367e-151">Lista</span><span class="sxs-lookup"><span data-stu-id="a367e-151">List</span></span>|  
|<span data-ttu-id="a367e-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="a367e-152">ListBox</span></span>|<span data-ttu-id="a367e-153">Lista</span><span class="sxs-lookup"><span data-stu-id="a367e-153">List</span></span>|  
|<span data-ttu-id="a367e-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="a367e-154">ListBox</span></span>|<span data-ttu-id="a367e-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="a367e-155">ListItem</span></span>|  
|<span data-ttu-id="a367e-156">#32768</span><span class="sxs-lookup"><span data-stu-id="a367e-156">#32768</span></span>|<span data-ttu-id="a367e-157">Menu</span><span class="sxs-lookup"><span data-stu-id="a367e-157">Menu</span></span>|  
|<span data-ttu-id="a367e-158">#32768</span><span class="sxs-lookup"><span data-stu-id="a367e-158">#32768</span></span>|<span data-ttu-id="a367e-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a367e-159">MenuItem</span></span>|  
|<span data-ttu-id="a367e-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="a367e-160">msctls_progress32</span></span>|<span data-ttu-id="a367e-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a367e-161">ProgressBar</span></span>|  
|<span data-ttu-id="a367e-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="a367e-162">RichEdit</span></span>|<span data-ttu-id="a367e-163">Document.</span><span class="sxs-lookup"><span data-stu-id="a367e-163">Document.</span></span> <span data-ttu-id="a367e-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="a367e-164">See note.</span></span>|  
|<span data-ttu-id="a367e-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="a367e-165">RichEdit20A</span></span>|<span data-ttu-id="a367e-166">Documento</span><span class="sxs-lookup"><span data-stu-id="a367e-166">Document</span></span>|  
|<span data-ttu-id="a367e-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="a367e-167">RichEdit20W</span></span>|<span data-ttu-id="a367e-168">Documento</span><span class="sxs-lookup"><span data-stu-id="a367e-168">Document</span></span>|  
|<span data-ttu-id="a367e-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="a367e-169">RichEdit50W</span></span>|<span data-ttu-id="a367e-170">Documento</span><span class="sxs-lookup"><span data-stu-id="a367e-170">Document</span></span>|  
|<span data-ttu-id="a367e-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="a367e-171">ScrollBar</span></span>|<span data-ttu-id="a367e-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a367e-172">Slider</span></span>|  
|<span data-ttu-id="a367e-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="a367e-173">msctls_trackbar32</span></span>|<span data-ttu-id="a367e-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a367e-174">Slider</span></span>|  
|<span data-ttu-id="a367e-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="a367e-175">msctls_updown32</span></span>|<span data-ttu-id="a367e-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="a367e-176">Spinner</span></span>|  
|<span data-ttu-id="a367e-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="a367e-177">msctls_statusbar32</span></span>|<span data-ttu-id="a367e-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a367e-178">StatusBar</span></span>|  
|<span data-ttu-id="a367e-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a367e-179">SysTabControl32</span></span>|<span data-ttu-id="a367e-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="a367e-180">Tab</span></span>|  
|<span data-ttu-id="a367e-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a367e-181">SysTabControl32</span></span>|<span data-ttu-id="a367e-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="a367e-182">TabItem</span></span>|  
|<span data-ttu-id="a367e-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-183">ToolbarWindow32</span></span>|<span data-ttu-id="a367e-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="a367e-184">ToolBar</span></span>|  
|<span data-ttu-id="a367e-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-185">ToolbarWindow32</span></span>|<span data-ttu-id="a367e-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a367e-186">MenuItem</span></span>|  
|<span data-ttu-id="a367e-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-187">ToolbarWindow32</span></span>|<span data-ttu-id="a367e-188">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-188">Button</span></span>|  
|<span data-ttu-id="a367e-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-189">ToolbarWindow32</span></span>|<span data-ttu-id="a367e-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a367e-190">CheckBox</span></span>|  
|<span data-ttu-id="a367e-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-191">ToolbarWindow32</span></span>|<span data-ttu-id="a367e-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a367e-192">RadioButton</span></span>|  
|<span data-ttu-id="a367e-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-193">ToolbarWindow32</span></span>|<span data-ttu-id="a367e-194">Separador</span><span class="sxs-lookup"><span data-stu-id="a367e-194">Separator</span></span>|  
|<span data-ttu-id="a367e-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="a367e-195">tooltips_class32</span></span>|<span data-ttu-id="a367e-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="a367e-196">ToolTip</span></span>|  
|<span data-ttu-id="a367e-197">#32774</span><span class="sxs-lookup"><span data-stu-id="a367e-197">#32774</span></span>|<span data-ttu-id="a367e-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="a367e-198">ToolTip</span></span>|  
|<span data-ttu-id="a367e-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="a367e-199">ReBarWindow32</span></span>|<span data-ttu-id="a367e-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a367e-200">Toolbar</span></span>|  
|<span data-ttu-id="a367e-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a367e-201">SysTreeView32</span></span>|<span data-ttu-id="a367e-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="a367e-202">Tree</span></span>|  
|<span data-ttu-id="a367e-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a367e-203">SysTreeView32</span></span>|<span data-ttu-id="a367e-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="a367e-204">TreeItem</span></span>|  
  
 <span data-ttu-id="a367e-205">**Observação** O controle RichEdit tem suporte apenas para as versões fornecidas [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] com (em Riched20. dll versão 3,1 e posterior e MsftEdit. dll versão 4,1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="a367e-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="a367e-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="a367e-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="a367e-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="a367e-207">Class name</span></span>|<span data-ttu-id="a367e-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="a367e-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a367e-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="a367e-209">SysAnimate32</span></span>|<span data-ttu-id="a367e-210">Image</span><span class="sxs-lookup"><span data-stu-id="a367e-210">Image</span></span>|  
|<span data-ttu-id="a367e-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="a367e-211">SysPager</span></span>|<span data-ttu-id="a367e-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="a367e-212">Spinner</span></span>|  
|<span data-ttu-id="a367e-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="a367e-213">SysDateTimePick32</span></span>|<span data-ttu-id="a367e-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="a367e-214">Custom</span></span>|  
|<span data-ttu-id="a367e-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="a367e-215">SysMonthCal32</span></span>|<span data-ttu-id="a367e-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="a367e-216">Calendar</span></span>|  
|<span data-ttu-id="a367e-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="a367e-217">MS_WINNOTE</span></span>|<span data-ttu-id="a367e-218">Dessa</span><span class="sxs-lookup"><span data-stu-id="a367e-218">Tooltip</span></span>|  
|<span data-ttu-id="a367e-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="a367e-219">VBBubble</span></span>|<span data-ttu-id="a367e-220">Dessa</span><span class="sxs-lookup"><span data-stu-id="a367e-220">Tooltip</span></span>|  
|<span data-ttu-id="a367e-221">ScrollBar (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="a367e-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="a367e-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a367e-222">Slider</span></span>|  
|<span data-ttu-id="a367e-223">Subgrade</span><span class="sxs-lookup"><span data-stu-id="a367e-223">SuperGrid</span></span>|<span data-ttu-id="a367e-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="a367e-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="a367e-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a367e-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="a367e-226">Os controles de Windows Forms são [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expostos a por meio de provedores do lado do cliente em UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="a367e-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a367e-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a367e-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a367e-228">Normalmente, Windows Forms controles que são wrappers gerenciados [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] para controles comuns são suportados [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pelo.</span><span class="sxs-lookup"><span data-stu-id="a367e-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a367e-229">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="a367e-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a367e-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="a367e-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="a367e-231">Botão</span><span class="sxs-lookup"><span data-stu-id="a367e-231">Button</span></span>|  
|<span data-ttu-id="a367e-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a367e-232">CheckBox</span></span>|  
|<span data-ttu-id="a367e-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="a367e-233">CheckedListBox</span></span>|  
|<span data-ttu-id="a367e-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a367e-234">ColorDialog</span></span>|  
|<span data-ttu-id="a367e-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a367e-235">ComboBox</span></span>|  
|<span data-ttu-id="a367e-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="a367e-236">FolderBrowser</span></span>|  
|<span data-ttu-id="a367e-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="a367e-237">FontDialog</span></span>|  
|<span data-ttu-id="a367e-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="a367e-238">GroupBox</span></span>|  
|<span data-ttu-id="a367e-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="a367e-239">HscrollBar</span></span>|  
|<span data-ttu-id="a367e-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="a367e-240">ImageList</span></span>|  
|<span data-ttu-id="a367e-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="a367e-241">Label</span></span>|  
|<span data-ttu-id="a367e-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="a367e-242">ListBox</span></span>|  
|<span data-ttu-id="a367e-243">ListView</span><span class="sxs-lookup"><span data-stu-id="a367e-243">ListView</span></span>|  
|<span data-ttu-id="a367e-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="a367e-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="a367e-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="a367e-245">MonthCalendar</span></span>|  
|<span data-ttu-id="a367e-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="a367e-246">NotifyIcon</span></span>|  
|<span data-ttu-id="a367e-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="a367e-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="a367e-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="a367e-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="a367e-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="a367e-249">PrintDialog</span></span>|  
|<span data-ttu-id="a367e-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a367e-250">ProgressBar</span></span>|  
|<span data-ttu-id="a367e-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a367e-251">RadioButton</span></span>|  
|<span data-ttu-id="a367e-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="a367e-252">RichTextBox</span></span>|  
|<span data-ttu-id="a367e-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="a367e-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="a367e-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="a367e-254">ScrollableControl</span></span>|  
|<span data-ttu-id="a367e-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="a367e-255">SoundPlayer</span></span>|  
|<span data-ttu-id="a367e-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a367e-256">StatusBar</span></span>|  
|<span data-ttu-id="a367e-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="a367e-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="a367e-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="a367e-258">TextBox</span></span>|  
|<span data-ttu-id="a367e-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="a367e-259">Timer</span></span>|  
|<span data-ttu-id="a367e-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a367e-260">Toolbar</span></span>|  
|<span data-ttu-id="a367e-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="a367e-261">ToolTip</span></span>|  
|<span data-ttu-id="a367e-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="a367e-262">TrackBar</span></span>|  
|<span data-ttu-id="a367e-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="a367e-263">TreeView</span></span>|  
|<span data-ttu-id="a367e-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="a367e-264">VscrollBar</span></span>|  
|<span data-ttu-id="a367e-265">Controlo</span><span class="sxs-lookup"><span data-stu-id="a367e-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="a367e-266">Os controles a seguir são expostos [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas por meio de seu suporte para o Microsoft acessibilidade ativa.</span><span class="sxs-lookup"><span data-stu-id="a367e-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="a367e-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a367e-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="a367e-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="a367e-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="a367e-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="a367e-269">BindingSource</span></span>|  
|<span data-ttu-id="a367e-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a367e-270">DataGrid</span></span>|  
|<span data-ttu-id="a367e-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="a367e-271">DataGridView</span></span>|  
|<span data-ttu-id="a367e-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="a367e-272">DataNavigator</span></span>|  
|<span data-ttu-id="a367e-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="a367e-273">DomainUpDown</span></span>|  
|<span data-ttu-id="a367e-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="a367e-274">ErrorProvider</span></span>|  
|<span data-ttu-id="a367e-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a367e-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="a367e-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="a367e-276">Form</span></span>|  
|<span data-ttu-id="a367e-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a367e-277">LinkLabel</span></span>|  
|<span data-ttu-id="a367e-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="a367e-278">HelpProvider</span></span>|  
|<span data-ttu-id="a367e-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="a367e-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="a367e-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="a367e-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="a367e-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="a367e-281">NumericUpDown</span></span>|  
|<span data-ttu-id="a367e-282">Painel</span><span class="sxs-lookup"><span data-stu-id="a367e-282">Panel</span></span>|  
|<span data-ttu-id="a367e-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="a367e-283">PictureBox</span></span>|  
|<span data-ttu-id="a367e-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="a367e-284">PrintDocument</span></span>|  
|<span data-ttu-id="a367e-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="a367e-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="a367e-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="a367e-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="a367e-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="a367e-287">PropertyGrid</span></span>|  
|<span data-ttu-id="a367e-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="a367e-288">UserControl</span></span>|  
|<span data-ttu-id="a367e-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a367e-289">ToolStrip</span></span>|  
|<span data-ttu-id="a367e-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a367e-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="a367e-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="a367e-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="a367e-292">Divisor</span><span class="sxs-lookup"><span data-stu-id="a367e-292">Splitter</span></span>|  
|<span data-ttu-id="a367e-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="a367e-293">RaftingContainer</span></span>|  
|<span data-ttu-id="a367e-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="a367e-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a367e-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a367e-295">See also</span></span>

- <span data-ttu-id="a367e-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="a367e-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)</span></span>
