---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 3fde9779205ea7d0902ddd99ed192f097a159d2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221473"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="a9833-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="a9833-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="a9833-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a9833-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a9833-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a9833-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a9833-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="a9833-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="a9833-106">Controles do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a9833-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="a9833-107">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte à interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9833-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a9833-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9833-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="a9833-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="a9833-109">Win32 Controls</span></span>  
 <span data-ttu-id="a9833-110">A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="a9833-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a9833-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a9833-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a9833-112">Suporte completo é fornecido somente para controles de versão 6 do Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="a9833-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="a9833-113">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="a9833-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a9833-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="a9833-114">Class name</span></span>|<span data-ttu-id="a9833-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="a9833-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a9833-116">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-116">Button</span></span>|<span data-ttu-id="a9833-117">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-117">Button</span></span>|  
|<span data-ttu-id="a9833-118">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-118">Button</span></span>|<span data-ttu-id="a9833-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a9833-119">RadioButton</span></span>|  
|<span data-ttu-id="a9833-120">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-120">Button</span></span>|<span data-ttu-id="a9833-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="a9833-121">Group</span></span>|  
|<span data-ttu-id="a9833-122">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-122">Button</span></span>|<span data-ttu-id="a9833-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a9833-123">CheckBox</span></span>|  
|<span data-ttu-id="a9833-124">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-124">Button</span></span>|<span data-ttu-id="a9833-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="a9833-125">Hyperlink</span></span>|  
|<span data-ttu-id="a9833-126">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-126">Button</span></span>|<span data-ttu-id="a9833-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="a9833-127">SplitButton</span></span>|  
|<span data-ttu-id="a9833-128">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-128">Button</span></span>|<span data-ttu-id="a9833-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a9833-129">CheckBox</span></span>|  
|<span data-ttu-id="a9833-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="a9833-130">ComboBoxEx32</span></span>|<span data-ttu-id="a9833-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a9833-131">ComboBox</span></span>|  
|<span data-ttu-id="a9833-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a9833-132">ComboBox</span></span>|<span data-ttu-id="a9833-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a9833-133">ComboBox</span></span>|  
|<span data-ttu-id="a9833-134">Editar</span><span class="sxs-lookup"><span data-stu-id="a9833-134">Edit</span></span>|<span data-ttu-id="a9833-135">Documento</span><span class="sxs-lookup"><span data-stu-id="a9833-135">Document</span></span>|  
|<span data-ttu-id="a9833-136">Editar</span><span class="sxs-lookup"><span data-stu-id="a9833-136">Edit</span></span>|<span data-ttu-id="a9833-137">Editar</span><span class="sxs-lookup"><span data-stu-id="a9833-137">Edit</span></span>|  
|<span data-ttu-id="a9833-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="a9833-138">SysLink</span></span>|<span data-ttu-id="a9833-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="a9833-139">Hyperlink</span></span>|  
|<span data-ttu-id="a9833-140">Estático</span><span class="sxs-lookup"><span data-stu-id="a9833-140">Static</span></span>|<span data-ttu-id="a9833-141">Texto</span><span class="sxs-lookup"><span data-stu-id="a9833-141">Text</span></span>|  
|<span data-ttu-id="a9833-142">Estático</span><span class="sxs-lookup"><span data-stu-id="a9833-142">Static</span></span>|<span data-ttu-id="a9833-143">Image</span><span class="sxs-lookup"><span data-stu-id="a9833-143">Image</span></span>|  
|<span data-ttu-id="a9833-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="a9833-144">SysIPAddress32</span></span>|<span data-ttu-id="a9833-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="a9833-145">Custom</span></span>|  
|<span data-ttu-id="a9833-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="a9833-146">SysHeader32</span></span>|<span data-ttu-id="a9833-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="a9833-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="a9833-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a9833-148">SysListView32</span></span>|<span data-ttu-id="a9833-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a9833-149">DataGrid</span></span>|  
|<span data-ttu-id="a9833-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a9833-150">SysListView32</span></span>|<span data-ttu-id="a9833-151">Lista</span><span class="sxs-lookup"><span data-stu-id="a9833-151">List</span></span>|  
|<span data-ttu-id="a9833-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="a9833-152">ListBox</span></span>|<span data-ttu-id="a9833-153">Lista</span><span class="sxs-lookup"><span data-stu-id="a9833-153">List</span></span>|  
|<span data-ttu-id="a9833-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="a9833-154">ListBox</span></span>|<span data-ttu-id="a9833-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="a9833-155">ListItem</span></span>|  
|<span data-ttu-id="a9833-156">#32768</span><span class="sxs-lookup"><span data-stu-id="a9833-156">#32768</span></span>|<span data-ttu-id="a9833-157">Menu</span><span class="sxs-lookup"><span data-stu-id="a9833-157">Menu</span></span>|  
|<span data-ttu-id="a9833-158">#32768</span><span class="sxs-lookup"><span data-stu-id="a9833-158">#32768</span></span>|<span data-ttu-id="a9833-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a9833-159">MenuItem</span></span>|  
|<span data-ttu-id="a9833-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="a9833-160">msctls_progress32</span></span>|<span data-ttu-id="a9833-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a9833-161">ProgressBar</span></span>|  
|<span data-ttu-id="a9833-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="a9833-162">RichEdit</span></span>|<span data-ttu-id="a9833-163">Documento.</span><span class="sxs-lookup"><span data-stu-id="a9833-163">Document.</span></span> <span data-ttu-id="a9833-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="a9833-164">See note.</span></span>|  
|<span data-ttu-id="a9833-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="a9833-165">RichEdit20A</span></span>|<span data-ttu-id="a9833-166">Documento</span><span class="sxs-lookup"><span data-stu-id="a9833-166">Document</span></span>|  
|<span data-ttu-id="a9833-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="a9833-167">RichEdit20W</span></span>|<span data-ttu-id="a9833-168">Documento</span><span class="sxs-lookup"><span data-stu-id="a9833-168">Document</span></span>|  
|<span data-ttu-id="a9833-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="a9833-169">RichEdit50W</span></span>|<span data-ttu-id="a9833-170">Documento</span><span class="sxs-lookup"><span data-stu-id="a9833-170">Document</span></span>|  
|<span data-ttu-id="a9833-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="a9833-171">ScrollBar</span></span>|<span data-ttu-id="a9833-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a9833-172">Slider</span></span>|  
|<span data-ttu-id="a9833-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="a9833-173">msctls_trackbar32</span></span>|<span data-ttu-id="a9833-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a9833-174">Slider</span></span>|  
|<span data-ttu-id="a9833-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="a9833-175">msctls_updown32</span></span>|<span data-ttu-id="a9833-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="a9833-176">Spinner</span></span>|  
|<span data-ttu-id="a9833-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="a9833-177">msctls_statusbar32</span></span>|<span data-ttu-id="a9833-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a9833-178">StatusBar</span></span>|  
|<span data-ttu-id="a9833-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a9833-179">SysTabControl32</span></span>|<span data-ttu-id="a9833-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="a9833-180">Tab</span></span>|  
|<span data-ttu-id="a9833-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a9833-181">SysTabControl32</span></span>|<span data-ttu-id="a9833-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="a9833-182">TabItem</span></span>|  
|<span data-ttu-id="a9833-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-183">ToolbarWindow32</span></span>|<span data-ttu-id="a9833-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="a9833-184">ToolBar</span></span>|  
|<span data-ttu-id="a9833-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-185">ToolbarWindow32</span></span>|<span data-ttu-id="a9833-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a9833-186">MenuItem</span></span>|  
|<span data-ttu-id="a9833-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-187">ToolbarWindow32</span></span>|<span data-ttu-id="a9833-188">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-188">Button</span></span>|  
|<span data-ttu-id="a9833-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-189">ToolbarWindow32</span></span>|<span data-ttu-id="a9833-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a9833-190">CheckBox</span></span>|  
|<span data-ttu-id="a9833-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-191">ToolbarWindow32</span></span>|<span data-ttu-id="a9833-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a9833-192">RadioButton</span></span>|  
|<span data-ttu-id="a9833-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-193">ToolbarWindow32</span></span>|<span data-ttu-id="a9833-194">Separador</span><span class="sxs-lookup"><span data-stu-id="a9833-194">Separator</span></span>|  
|<span data-ttu-id="a9833-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="a9833-195">tooltips_class32</span></span>|<span data-ttu-id="a9833-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="a9833-196">ToolTip</span></span>|  
|<span data-ttu-id="a9833-197">#32774</span><span class="sxs-lookup"><span data-stu-id="a9833-197">#32774</span></span>|<span data-ttu-id="a9833-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="a9833-198">ToolTip</span></span>|  
|<span data-ttu-id="a9833-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="a9833-199">ReBarWindow32</span></span>|<span data-ttu-id="a9833-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a9833-200">Toolbar</span></span>|  
|<span data-ttu-id="a9833-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a9833-201">SysTreeView32</span></span>|<span data-ttu-id="a9833-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="a9833-202">Tree</span></span>|  
|<span data-ttu-id="a9833-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a9833-203">SysTreeView32</span></span>|<span data-ttu-id="a9833-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="a9833-204">TreeItem</span></span>|  
  
 <span data-ttu-id="a9833-205">**Observação** RichEdit o controle tem suporte somente para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (em RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posteriores).</span><span class="sxs-lookup"><span data-stu-id="a9833-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="a9833-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="a9833-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="a9833-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="a9833-207">Class name</span></span>|<span data-ttu-id="a9833-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="a9833-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a9833-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="a9833-209">SysAnimate32</span></span>|<span data-ttu-id="a9833-210">Image</span><span class="sxs-lookup"><span data-stu-id="a9833-210">Image</span></span>|  
|<span data-ttu-id="a9833-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="a9833-211">SysPager</span></span>|<span data-ttu-id="a9833-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="a9833-212">Spinner</span></span>|  
|<span data-ttu-id="a9833-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="a9833-213">SysDateTimePick32</span></span>|<span data-ttu-id="a9833-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="a9833-214">Custom</span></span>|  
|<span data-ttu-id="a9833-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="a9833-215">SysMonthCal32</span></span>|<span data-ttu-id="a9833-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="a9833-216">Calendar</span></span>|  
|<span data-ttu-id="a9833-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="a9833-217">MS_WINNOTE</span></span>|<span data-ttu-id="a9833-218">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="a9833-218">Tooltip</span></span>|  
|<span data-ttu-id="a9833-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="a9833-219">VBBubble</span></span>|<span data-ttu-id="a9833-220">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="a9833-220">Tooltip</span></span>|  
|<span data-ttu-id="a9833-221">Barra de rolagem (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="a9833-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="a9833-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a9833-222">Slider</span></span>|  
|<span data-ttu-id="a9833-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="a9833-223">SuperGrid</span></span>|<span data-ttu-id="a9833-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="a9833-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="a9833-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9833-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="a9833-226">Controles dos Windows Forms são expostos ao [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="a9833-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a9833-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a9833-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a9833-228">Normalmente, controles de formulários do Windows que são gerenciados wrappers [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9833-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a9833-229">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="a9833-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a9833-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="a9833-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="a9833-231">Botão</span><span class="sxs-lookup"><span data-stu-id="a9833-231">Button</span></span>|  
|<span data-ttu-id="a9833-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a9833-232">CheckBox</span></span>|  
|<span data-ttu-id="a9833-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="a9833-233">CheckedListBox</span></span>|  
|<span data-ttu-id="a9833-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a9833-234">ColorDialog</span></span>|  
|<span data-ttu-id="a9833-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a9833-235">ComboBox</span></span>|  
|<span data-ttu-id="a9833-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="a9833-236">FolderBrowser</span></span>|  
|<span data-ttu-id="a9833-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="a9833-237">FontDialog</span></span>|  
|<span data-ttu-id="a9833-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="a9833-238">GroupBox</span></span>|  
|<span data-ttu-id="a9833-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="a9833-239">HscrollBar</span></span>|  
|<span data-ttu-id="a9833-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="a9833-240">ImageList</span></span>|  
|<span data-ttu-id="a9833-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="a9833-241">Label</span></span>|  
|<span data-ttu-id="a9833-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="a9833-242">ListBox</span></span>|  
|<span data-ttu-id="a9833-243">ListView</span><span class="sxs-lookup"><span data-stu-id="a9833-243">ListView</span></span>|  
|<span data-ttu-id="a9833-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="a9833-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="a9833-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="a9833-245">MonthCalendar</span></span>|  
|<span data-ttu-id="a9833-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="a9833-246">NotifyIcon</span></span>|  
|<span data-ttu-id="a9833-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="a9833-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="a9833-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="a9833-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="a9833-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="a9833-249">PrintDialog</span></span>|  
|<span data-ttu-id="a9833-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a9833-250">ProgressBar</span></span>|  
|<span data-ttu-id="a9833-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a9833-251">RadioButton</span></span>|  
|<span data-ttu-id="a9833-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="a9833-252">RichTextBox</span></span>|  
|<span data-ttu-id="a9833-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="a9833-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="a9833-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="a9833-254">ScrollableControl</span></span>|  
|<span data-ttu-id="a9833-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="a9833-255">SoundPlayer</span></span>|  
|<span data-ttu-id="a9833-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a9833-256">StatusBar</span></span>|  
|<span data-ttu-id="a9833-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="a9833-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="a9833-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="a9833-258">TextBox</span></span>|  
|<span data-ttu-id="a9833-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="a9833-259">Timer</span></span>|  
|<span data-ttu-id="a9833-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a9833-260">Toolbar</span></span>|  
|<span data-ttu-id="a9833-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="a9833-261">ToolTip</span></span>|  
|<span data-ttu-id="a9833-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="a9833-262">TrackBar</span></span>|  
|<span data-ttu-id="a9833-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="a9833-263">TreeView</span></span>|  
|<span data-ttu-id="a9833-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="a9833-264">VscrollBar</span></span>|  
|<span data-ttu-id="a9833-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="a9833-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="a9833-266">Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] somente através de seu suporte [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9833-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="a9833-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a9833-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="a9833-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="a9833-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="a9833-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="a9833-269">BindingSource</span></span>|  
|<span data-ttu-id="a9833-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a9833-270">DataGrid</span></span>|  
|<span data-ttu-id="a9833-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="a9833-271">DataGridView</span></span>|  
|<span data-ttu-id="a9833-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="a9833-272">DataNavigator</span></span>|  
|<span data-ttu-id="a9833-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="a9833-273">DomainUpDown</span></span>|  
|<span data-ttu-id="a9833-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="a9833-274">ErrorProvider</span></span>|  
|<span data-ttu-id="a9833-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a9833-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="a9833-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="a9833-276">Form</span></span>|  
|<span data-ttu-id="a9833-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a9833-277">LinkLabel</span></span>|  
|<span data-ttu-id="a9833-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="a9833-278">HelpProvider</span></span>|  
|<span data-ttu-id="a9833-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="a9833-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="a9833-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="a9833-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="a9833-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="a9833-281">NumericUpDown</span></span>|  
|<span data-ttu-id="a9833-282">Painel</span><span class="sxs-lookup"><span data-stu-id="a9833-282">Panel</span></span>|  
|<span data-ttu-id="a9833-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="a9833-283">PictureBox</span></span>|  
|<span data-ttu-id="a9833-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="a9833-284">PrintDocument</span></span>|  
|<span data-ttu-id="a9833-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="a9833-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="a9833-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="a9833-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="a9833-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="a9833-287">PropertyGrid</span></span>|  
|<span data-ttu-id="a9833-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="a9833-288">UserControl</span></span>|  
|<span data-ttu-id="a9833-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a9833-289">ToolStrip</span></span>|  
|<span data-ttu-id="a9833-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a9833-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="a9833-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="a9833-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="a9833-292">Divisor</span><span class="sxs-lookup"><span data-stu-id="a9833-292">Splitter</span></span>|  
|<span data-ttu-id="a9833-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="a9833-293">RaftingContainer</span></span>|  
|<span data-ttu-id="a9833-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="a9833-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9833-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9833-295">See also</span></span>

- [<span data-ttu-id="a9833-296">Tipos de controle de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a9833-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
