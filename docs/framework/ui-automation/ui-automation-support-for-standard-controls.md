---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 641fc3f8dfca3ff6506354c076b98cc88073a1b7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802113"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="c3979-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="c3979-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="c3979-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c3979-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c3979-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="c3979-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c3979-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="c3979-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="c3979-106">Controles do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="c3979-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="c3979-107">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte à interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3979-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="c3979-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3979-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="c3979-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="c3979-109">Win32 Controls</span></span>  
 <span data-ttu-id="c3979-110">A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="c3979-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="c3979-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c3979-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="c3979-112">Suporte completo é fornecido somente para controles de versão 6 do Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="c3979-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="c3979-113">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="c3979-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="c3979-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="c3979-114">Class name</span></span>|<span data-ttu-id="c3979-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="c3979-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="c3979-116">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-116">Button</span></span>|<span data-ttu-id="c3979-117">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-117">Button</span></span>|  
|<span data-ttu-id="c3979-118">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-118">Button</span></span>|<span data-ttu-id="c3979-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="c3979-119">RadioButton</span></span>|  
|<span data-ttu-id="c3979-120">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-120">Button</span></span>|<span data-ttu-id="c3979-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="c3979-121">Group</span></span>|  
|<span data-ttu-id="c3979-122">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-122">Button</span></span>|<span data-ttu-id="c3979-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c3979-123">CheckBox</span></span>|  
|<span data-ttu-id="c3979-124">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-124">Button</span></span>|<span data-ttu-id="c3979-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="c3979-125">Hyperlink</span></span>|  
|<span data-ttu-id="c3979-126">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-126">Button</span></span>|<span data-ttu-id="c3979-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="c3979-127">SplitButton</span></span>|  
|<span data-ttu-id="c3979-128">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-128">Button</span></span>|<span data-ttu-id="c3979-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c3979-129">CheckBox</span></span>|  
|<span data-ttu-id="c3979-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="c3979-130">ComboBoxEx32</span></span>|<span data-ttu-id="c3979-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c3979-131">ComboBox</span></span>|  
|<span data-ttu-id="c3979-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c3979-132">ComboBox</span></span>|<span data-ttu-id="c3979-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c3979-133">ComboBox</span></span>|  
|<span data-ttu-id="c3979-134">Editar</span><span class="sxs-lookup"><span data-stu-id="c3979-134">Edit</span></span>|<span data-ttu-id="c3979-135">Documento</span><span class="sxs-lookup"><span data-stu-id="c3979-135">Document</span></span>|  
|<span data-ttu-id="c3979-136">Editar</span><span class="sxs-lookup"><span data-stu-id="c3979-136">Edit</span></span>|<span data-ttu-id="c3979-137">Editar</span><span class="sxs-lookup"><span data-stu-id="c3979-137">Edit</span></span>|  
|<span data-ttu-id="c3979-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="c3979-138">SysLink</span></span>|<span data-ttu-id="c3979-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="c3979-139">Hyperlink</span></span>|  
|<span data-ttu-id="c3979-140">Estático</span><span class="sxs-lookup"><span data-stu-id="c3979-140">Static</span></span>|<span data-ttu-id="c3979-141">Texto</span><span class="sxs-lookup"><span data-stu-id="c3979-141">Text</span></span>|  
|<span data-ttu-id="c3979-142">Estático</span><span class="sxs-lookup"><span data-stu-id="c3979-142">Static</span></span>|<span data-ttu-id="c3979-143">Image</span><span class="sxs-lookup"><span data-stu-id="c3979-143">Image</span></span>|  
|<span data-ttu-id="c3979-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="c3979-144">SysIPAddress32</span></span>|<span data-ttu-id="c3979-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="c3979-145">Custom</span></span>|  
|<span data-ttu-id="c3979-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="c3979-146">SysHeader32</span></span>|<span data-ttu-id="c3979-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="c3979-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="c3979-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="c3979-148">SysListView32</span></span>|<span data-ttu-id="c3979-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="c3979-149">DataGrid</span></span>|  
|<span data-ttu-id="c3979-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="c3979-150">SysListView32</span></span>|<span data-ttu-id="c3979-151">Lista</span><span class="sxs-lookup"><span data-stu-id="c3979-151">List</span></span>|  
|<span data-ttu-id="c3979-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="c3979-152">ListBox</span></span>|<span data-ttu-id="c3979-153">Lista</span><span class="sxs-lookup"><span data-stu-id="c3979-153">List</span></span>|  
|<span data-ttu-id="c3979-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="c3979-154">ListBox</span></span>|<span data-ttu-id="c3979-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="c3979-155">ListItem</span></span>|  
|<span data-ttu-id="c3979-156">#32768</span><span class="sxs-lookup"><span data-stu-id="c3979-156">#32768</span></span>|<span data-ttu-id="c3979-157">Menu</span><span class="sxs-lookup"><span data-stu-id="c3979-157">Menu</span></span>|  
|<span data-ttu-id="c3979-158">#32768</span><span class="sxs-lookup"><span data-stu-id="c3979-158">#32768</span></span>|<span data-ttu-id="c3979-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="c3979-159">MenuItem</span></span>|  
|<span data-ttu-id="c3979-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="c3979-160">msctls_progress32</span></span>|<span data-ttu-id="c3979-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="c3979-161">ProgressBar</span></span>|  
|<span data-ttu-id="c3979-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="c3979-162">RichEdit</span></span>|<span data-ttu-id="c3979-163">Documento.</span><span class="sxs-lookup"><span data-stu-id="c3979-163">Document.</span></span> <span data-ttu-id="c3979-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="c3979-164">See note.</span></span>|  
|<span data-ttu-id="c3979-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="c3979-165">RichEdit20A</span></span>|<span data-ttu-id="c3979-166">Documento</span><span class="sxs-lookup"><span data-stu-id="c3979-166">Document</span></span>|  
|<span data-ttu-id="c3979-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="c3979-167">RichEdit20W</span></span>|<span data-ttu-id="c3979-168">Documento</span><span class="sxs-lookup"><span data-stu-id="c3979-168">Document</span></span>|  
|<span data-ttu-id="c3979-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="c3979-169">RichEdit50W</span></span>|<span data-ttu-id="c3979-170">Documento</span><span class="sxs-lookup"><span data-stu-id="c3979-170">Document</span></span>|  
|<span data-ttu-id="c3979-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="c3979-171">ScrollBar</span></span>|<span data-ttu-id="c3979-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="c3979-172">Slider</span></span>|  
|<span data-ttu-id="c3979-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="c3979-173">msctls_trackbar32</span></span>|<span data-ttu-id="c3979-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="c3979-174">Slider</span></span>|  
|<span data-ttu-id="c3979-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="c3979-175">msctls_updown32</span></span>|<span data-ttu-id="c3979-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="c3979-176">Spinner</span></span>|  
|<span data-ttu-id="c3979-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="c3979-177">msctls_statusbar32</span></span>|<span data-ttu-id="c3979-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="c3979-178">StatusBar</span></span>|  
|<span data-ttu-id="c3979-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="c3979-179">SysTabControl32</span></span>|<span data-ttu-id="c3979-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="c3979-180">Tab</span></span>|  
|<span data-ttu-id="c3979-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="c3979-181">SysTabControl32</span></span>|<span data-ttu-id="c3979-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="c3979-182">TabItem</span></span>|  
|<span data-ttu-id="c3979-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-183">ToolbarWindow32</span></span>|<span data-ttu-id="c3979-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="c3979-184">ToolBar</span></span>|  
|<span data-ttu-id="c3979-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-185">ToolbarWindow32</span></span>|<span data-ttu-id="c3979-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="c3979-186">MenuItem</span></span>|  
|<span data-ttu-id="c3979-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-187">ToolbarWindow32</span></span>|<span data-ttu-id="c3979-188">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-188">Button</span></span>|  
|<span data-ttu-id="c3979-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-189">ToolbarWindow32</span></span>|<span data-ttu-id="c3979-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c3979-190">CheckBox</span></span>|  
|<span data-ttu-id="c3979-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-191">ToolbarWindow32</span></span>|<span data-ttu-id="c3979-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="c3979-192">RadioButton</span></span>|  
|<span data-ttu-id="c3979-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-193">ToolbarWindow32</span></span>|<span data-ttu-id="c3979-194">Separador</span><span class="sxs-lookup"><span data-stu-id="c3979-194">Separator</span></span>|  
|<span data-ttu-id="c3979-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="c3979-195">tooltips_class32</span></span>|<span data-ttu-id="c3979-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="c3979-196">ToolTip</span></span>|  
|<span data-ttu-id="c3979-197">#32774</span><span class="sxs-lookup"><span data-stu-id="c3979-197">#32774</span></span>|<span data-ttu-id="c3979-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="c3979-198">ToolTip</span></span>|  
|<span data-ttu-id="c3979-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="c3979-199">ReBarWindow32</span></span>|<span data-ttu-id="c3979-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="c3979-200">Toolbar</span></span>|  
|<span data-ttu-id="c3979-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="c3979-201">SysTreeView32</span></span>|<span data-ttu-id="c3979-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="c3979-202">Tree</span></span>|  
|<span data-ttu-id="c3979-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="c3979-203">SysTreeView32</span></span>|<span data-ttu-id="c3979-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="c3979-204">TreeItem</span></span>|  
  
 <span data-ttu-id="c3979-205">**Observação** RichEdit o controle tem suporte somente para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (em RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posteriores).</span><span class="sxs-lookup"><span data-stu-id="c3979-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="c3979-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="c3979-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="c3979-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="c3979-207">Class name</span></span>|<span data-ttu-id="c3979-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="c3979-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="c3979-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="c3979-209">SysAnimate32</span></span>|<span data-ttu-id="c3979-210">Image</span><span class="sxs-lookup"><span data-stu-id="c3979-210">Image</span></span>|  
|<span data-ttu-id="c3979-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="c3979-211">SysPager</span></span>|<span data-ttu-id="c3979-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="c3979-212">Spinner</span></span>|  
|<span data-ttu-id="c3979-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="c3979-213">SysDateTimePick32</span></span>|<span data-ttu-id="c3979-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="c3979-214">Custom</span></span>|  
|<span data-ttu-id="c3979-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="c3979-215">SysMonthCal32</span></span>|<span data-ttu-id="c3979-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="c3979-216">Calendar</span></span>|  
|<span data-ttu-id="c3979-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="c3979-217">MS_WINNOTE</span></span>|<span data-ttu-id="c3979-218">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="c3979-218">Tooltip</span></span>|  
|<span data-ttu-id="c3979-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="c3979-219">VBBubble</span></span>|<span data-ttu-id="c3979-220">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="c3979-220">Tooltip</span></span>|  
|<span data-ttu-id="c3979-221">Barra de rolagem (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="c3979-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="c3979-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="c3979-222">Slider</span></span>|  
|<span data-ttu-id="c3979-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="c3979-223">SuperGrid</span></span>|<span data-ttu-id="c3979-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="c3979-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="c3979-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c3979-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="c3979-226">Controles dos Windows Forms são expostos ao [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="c3979-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="c3979-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c3979-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="c3979-228">Normalmente, controles de formulários do Windows que são gerenciados wrappers [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3979-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="c3979-229">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="c3979-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="c3979-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="c3979-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="c3979-231">Botão</span><span class="sxs-lookup"><span data-stu-id="c3979-231">Button</span></span>|  
|<span data-ttu-id="c3979-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c3979-232">CheckBox</span></span>|  
|<span data-ttu-id="c3979-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="c3979-233">CheckedListBox</span></span>|  
|<span data-ttu-id="c3979-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="c3979-234">ColorDialog</span></span>|  
|<span data-ttu-id="c3979-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c3979-235">ComboBox</span></span>|  
|<span data-ttu-id="c3979-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="c3979-236">FolderBrowser</span></span>|  
|<span data-ttu-id="c3979-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="c3979-237">FontDialog</span></span>|  
|<span data-ttu-id="c3979-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="c3979-238">GroupBox</span></span>|  
|<span data-ttu-id="c3979-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="c3979-239">HscrollBar</span></span>|  
|<span data-ttu-id="c3979-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="c3979-240">ImageList</span></span>|  
|<span data-ttu-id="c3979-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="c3979-241">Label</span></span>|  
|<span data-ttu-id="c3979-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="c3979-242">ListBox</span></span>|  
|<span data-ttu-id="c3979-243">ListView</span><span class="sxs-lookup"><span data-stu-id="c3979-243">ListView</span></span>|  
|<span data-ttu-id="c3979-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c3979-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="c3979-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="c3979-245">MonthCalendar</span></span>|  
|<span data-ttu-id="c3979-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="c3979-246">NotifyIcon</span></span>|  
|<span data-ttu-id="c3979-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="c3979-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="c3979-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="c3979-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="c3979-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="c3979-249">PrintDialog</span></span>|  
|<span data-ttu-id="c3979-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="c3979-250">ProgressBar</span></span>|  
|<span data-ttu-id="c3979-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="c3979-251">RadioButton</span></span>|  
|<span data-ttu-id="c3979-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c3979-252">RichTextBox</span></span>|  
|<span data-ttu-id="c3979-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c3979-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="c3979-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="c3979-254">ScrollableControl</span></span>|  
|<span data-ttu-id="c3979-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="c3979-255">SoundPlayer</span></span>|  
|<span data-ttu-id="c3979-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="c3979-256">StatusBar</span></span>|  
|<span data-ttu-id="c3979-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="c3979-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="c3979-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="c3979-258">TextBox</span></span>|  
|<span data-ttu-id="c3979-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="c3979-259">Timer</span></span>|  
|<span data-ttu-id="c3979-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="c3979-260">Toolbar</span></span>|  
|<span data-ttu-id="c3979-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="c3979-261">ToolTip</span></span>|  
|<span data-ttu-id="c3979-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="c3979-262">TrackBar</span></span>|  
|<span data-ttu-id="c3979-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="c3979-263">TreeView</span></span>|  
|<span data-ttu-id="c3979-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="c3979-264">VscrollBar</span></span>|  
|<span data-ttu-id="c3979-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="c3979-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="c3979-266">Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] somente através de seu suporte para Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="c3979-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="c3979-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c3979-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="c3979-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="c3979-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="c3979-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="c3979-269">BindingSource</span></span>|  
|<span data-ttu-id="c3979-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="c3979-270">DataGrid</span></span>|  
|<span data-ttu-id="c3979-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="c3979-271">DataGridView</span></span>|  
|<span data-ttu-id="c3979-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="c3979-272">DataNavigator</span></span>|  
|<span data-ttu-id="c3979-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="c3979-273">DomainUpDown</span></span>|  
|<span data-ttu-id="c3979-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="c3979-274">ErrorProvider</span></span>|  
|<span data-ttu-id="c3979-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c3979-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="c3979-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="c3979-276">Form</span></span>|  
|<span data-ttu-id="c3979-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="c3979-277">LinkLabel</span></span>|  
|<span data-ttu-id="c3979-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="c3979-278">HelpProvider</span></span>|  
|<span data-ttu-id="c3979-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c3979-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="c3979-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="c3979-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="c3979-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="c3979-281">NumericUpDown</span></span>|  
|<span data-ttu-id="c3979-282">Painel</span><span class="sxs-lookup"><span data-stu-id="c3979-282">Panel</span></span>|  
|<span data-ttu-id="c3979-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="c3979-283">PictureBox</span></span>|  
|<span data-ttu-id="c3979-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="c3979-284">PrintDocument</span></span>|  
|<span data-ttu-id="c3979-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="c3979-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="c3979-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="c3979-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="c3979-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="c3979-287">PropertyGrid</span></span>|  
|<span data-ttu-id="c3979-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="c3979-288">UserControl</span></span>|  
|<span data-ttu-id="c3979-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c3979-289">ToolStrip</span></span>|  
|<span data-ttu-id="c3979-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c3979-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="c3979-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="c3979-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="c3979-292">Divisor</span><span class="sxs-lookup"><span data-stu-id="c3979-292">Splitter</span></span>|  
|<span data-ttu-id="c3979-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="c3979-293">RaftingContainer</span></span>|  
|<span data-ttu-id="c3979-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="c3979-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3979-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3979-295">See also</span></span>

- <span data-ttu-id="c3979-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="c3979-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)</span></span>
