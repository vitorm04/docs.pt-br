---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 5dbd547378faf885f5d0349ff77d124b0b860591
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677624"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="ae179-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="ae179-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="ae179-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ae179-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ae179-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ae179-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ae179-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="ae179-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="ae179-106">Controles do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="ae179-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="ae179-107">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte à interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae179-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="ae179-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae179-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="ae179-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="ae179-109">Win32 Controls</span></span>  
 <span data-ttu-id="ae179-110">A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="ae179-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="ae179-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="ae179-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="ae179-112">Suporte completo é fornecido somente para controles de versão 6 do Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="ae179-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="ae179-113">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="ae179-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="ae179-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="ae179-114">Class name</span></span>|<span data-ttu-id="ae179-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="ae179-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ae179-116">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-116">Button</span></span>|<span data-ttu-id="ae179-117">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-117">Button</span></span>|  
|<span data-ttu-id="ae179-118">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-118">Button</span></span>|<span data-ttu-id="ae179-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ae179-119">RadioButton</span></span>|  
|<span data-ttu-id="ae179-120">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-120">Button</span></span>|<span data-ttu-id="ae179-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="ae179-121">Group</span></span>|  
|<span data-ttu-id="ae179-122">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-122">Button</span></span>|<span data-ttu-id="ae179-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ae179-123">CheckBox</span></span>|  
|<span data-ttu-id="ae179-124">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-124">Button</span></span>|<span data-ttu-id="ae179-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="ae179-125">Hyperlink</span></span>|  
|<span data-ttu-id="ae179-126">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-126">Button</span></span>|<span data-ttu-id="ae179-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="ae179-127">SplitButton</span></span>|  
|<span data-ttu-id="ae179-128">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-128">Button</span></span>|<span data-ttu-id="ae179-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ae179-129">CheckBox</span></span>|  
|<span data-ttu-id="ae179-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="ae179-130">ComboBoxEx32</span></span>|<span data-ttu-id="ae179-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ae179-131">ComboBox</span></span>|  
|<span data-ttu-id="ae179-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ae179-132">ComboBox</span></span>|<span data-ttu-id="ae179-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ae179-133">ComboBox</span></span>|  
|<span data-ttu-id="ae179-134">Editar</span><span class="sxs-lookup"><span data-stu-id="ae179-134">Edit</span></span>|<span data-ttu-id="ae179-135">Documento</span><span class="sxs-lookup"><span data-stu-id="ae179-135">Document</span></span>|  
|<span data-ttu-id="ae179-136">Editar</span><span class="sxs-lookup"><span data-stu-id="ae179-136">Edit</span></span>|<span data-ttu-id="ae179-137">Editar</span><span class="sxs-lookup"><span data-stu-id="ae179-137">Edit</span></span>|  
|<span data-ttu-id="ae179-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="ae179-138">SysLink</span></span>|<span data-ttu-id="ae179-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="ae179-139">Hyperlink</span></span>|  
|<span data-ttu-id="ae179-140">Estático</span><span class="sxs-lookup"><span data-stu-id="ae179-140">Static</span></span>|<span data-ttu-id="ae179-141">Texto</span><span class="sxs-lookup"><span data-stu-id="ae179-141">Text</span></span>|  
|<span data-ttu-id="ae179-142">Estático</span><span class="sxs-lookup"><span data-stu-id="ae179-142">Static</span></span>|<span data-ttu-id="ae179-143">Image</span><span class="sxs-lookup"><span data-stu-id="ae179-143">Image</span></span>|  
|<span data-ttu-id="ae179-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="ae179-144">SysIPAddress32</span></span>|<span data-ttu-id="ae179-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="ae179-145">Custom</span></span>|  
|<span data-ttu-id="ae179-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="ae179-146">SysHeader32</span></span>|<span data-ttu-id="ae179-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="ae179-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="ae179-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="ae179-148">SysListView32</span></span>|<span data-ttu-id="ae179-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ae179-149">DataGrid</span></span>|  
|<span data-ttu-id="ae179-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="ae179-150">SysListView32</span></span>|<span data-ttu-id="ae179-151">Lista</span><span class="sxs-lookup"><span data-stu-id="ae179-151">List</span></span>|  
|<span data-ttu-id="ae179-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="ae179-152">ListBox</span></span>|<span data-ttu-id="ae179-153">Lista</span><span class="sxs-lookup"><span data-stu-id="ae179-153">List</span></span>|  
|<span data-ttu-id="ae179-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="ae179-154">ListBox</span></span>|<span data-ttu-id="ae179-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="ae179-155">ListItem</span></span>|  
|<span data-ttu-id="ae179-156">#32768</span><span class="sxs-lookup"><span data-stu-id="ae179-156">#32768</span></span>|<span data-ttu-id="ae179-157">Menu</span><span class="sxs-lookup"><span data-stu-id="ae179-157">Menu</span></span>|  
|<span data-ttu-id="ae179-158">#32768</span><span class="sxs-lookup"><span data-stu-id="ae179-158">#32768</span></span>|<span data-ttu-id="ae179-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ae179-159">MenuItem</span></span>|  
|<span data-ttu-id="ae179-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="ae179-160">msctls_progress32</span></span>|<span data-ttu-id="ae179-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ae179-161">ProgressBar</span></span>|  
|<span data-ttu-id="ae179-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="ae179-162">RichEdit</span></span>|<span data-ttu-id="ae179-163">Documento.</span><span class="sxs-lookup"><span data-stu-id="ae179-163">Document.</span></span> <span data-ttu-id="ae179-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="ae179-164">See note.</span></span>|  
|<span data-ttu-id="ae179-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="ae179-165">RichEdit20A</span></span>|<span data-ttu-id="ae179-166">Documento</span><span class="sxs-lookup"><span data-stu-id="ae179-166">Document</span></span>|  
|<span data-ttu-id="ae179-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="ae179-167">RichEdit20W</span></span>|<span data-ttu-id="ae179-168">Documento</span><span class="sxs-lookup"><span data-stu-id="ae179-168">Document</span></span>|  
|<span data-ttu-id="ae179-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="ae179-169">RichEdit50W</span></span>|<span data-ttu-id="ae179-170">Documento</span><span class="sxs-lookup"><span data-stu-id="ae179-170">Document</span></span>|  
|<span data-ttu-id="ae179-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="ae179-171">ScrollBar</span></span>|<span data-ttu-id="ae179-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="ae179-172">Slider</span></span>|  
|<span data-ttu-id="ae179-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="ae179-173">msctls_trackbar32</span></span>|<span data-ttu-id="ae179-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="ae179-174">Slider</span></span>|  
|<span data-ttu-id="ae179-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="ae179-175">msctls_updown32</span></span>|<span data-ttu-id="ae179-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="ae179-176">Spinner</span></span>|  
|<span data-ttu-id="ae179-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="ae179-177">msctls_statusbar32</span></span>|<span data-ttu-id="ae179-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="ae179-178">StatusBar</span></span>|  
|<span data-ttu-id="ae179-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="ae179-179">SysTabControl32</span></span>|<span data-ttu-id="ae179-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="ae179-180">Tab</span></span>|  
|<span data-ttu-id="ae179-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="ae179-181">SysTabControl32</span></span>|<span data-ttu-id="ae179-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="ae179-182">TabItem</span></span>|  
|<span data-ttu-id="ae179-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-183">ToolbarWindow32</span></span>|<span data-ttu-id="ae179-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="ae179-184">ToolBar</span></span>|  
|<span data-ttu-id="ae179-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-185">ToolbarWindow32</span></span>|<span data-ttu-id="ae179-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ae179-186">MenuItem</span></span>|  
|<span data-ttu-id="ae179-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-187">ToolbarWindow32</span></span>|<span data-ttu-id="ae179-188">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-188">Button</span></span>|  
|<span data-ttu-id="ae179-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-189">ToolbarWindow32</span></span>|<span data-ttu-id="ae179-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ae179-190">CheckBox</span></span>|  
|<span data-ttu-id="ae179-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-191">ToolbarWindow32</span></span>|<span data-ttu-id="ae179-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ae179-192">RadioButton</span></span>|  
|<span data-ttu-id="ae179-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-193">ToolbarWindow32</span></span>|<span data-ttu-id="ae179-194">Separador</span><span class="sxs-lookup"><span data-stu-id="ae179-194">Separator</span></span>|  
|<span data-ttu-id="ae179-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="ae179-195">tooltips_class32</span></span>|<span data-ttu-id="ae179-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ae179-196">ToolTip</span></span>|  
|<span data-ttu-id="ae179-197">#32774</span><span class="sxs-lookup"><span data-stu-id="ae179-197">#32774</span></span>|<span data-ttu-id="ae179-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ae179-198">ToolTip</span></span>|  
|<span data-ttu-id="ae179-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="ae179-199">ReBarWindow32</span></span>|<span data-ttu-id="ae179-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="ae179-200">Toolbar</span></span>|  
|<span data-ttu-id="ae179-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="ae179-201">SysTreeView32</span></span>|<span data-ttu-id="ae179-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="ae179-202">Tree</span></span>|  
|<span data-ttu-id="ae179-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="ae179-203">SysTreeView32</span></span>|<span data-ttu-id="ae179-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="ae179-204">TreeItem</span></span>|  
  
 <span data-ttu-id="ae179-205">**Observação** RichEdit o controle tem suporte somente para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (em RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posteriores).</span><span class="sxs-lookup"><span data-stu-id="ae179-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="ae179-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="ae179-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="ae179-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="ae179-207">Class name</span></span>|<span data-ttu-id="ae179-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="ae179-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ae179-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="ae179-209">SysAnimate32</span></span>|<span data-ttu-id="ae179-210">Image</span><span class="sxs-lookup"><span data-stu-id="ae179-210">Image</span></span>|  
|<span data-ttu-id="ae179-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="ae179-211">SysPager</span></span>|<span data-ttu-id="ae179-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="ae179-212">Spinner</span></span>|  
|<span data-ttu-id="ae179-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="ae179-213">SysDateTimePick32</span></span>|<span data-ttu-id="ae179-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="ae179-214">Custom</span></span>|  
|<span data-ttu-id="ae179-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="ae179-215">SysMonthCal32</span></span>|<span data-ttu-id="ae179-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="ae179-216">Calendar</span></span>|  
|<span data-ttu-id="ae179-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="ae179-217">MS_WINNOTE</span></span>|<span data-ttu-id="ae179-218">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="ae179-218">Tooltip</span></span>|  
|<span data-ttu-id="ae179-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="ae179-219">VBBubble</span></span>|<span data-ttu-id="ae179-220">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="ae179-220">Tooltip</span></span>|  
|<span data-ttu-id="ae179-221">Barra de rolagem (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="ae179-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="ae179-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="ae179-222">Slider</span></span>|  
|<span data-ttu-id="ae179-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="ae179-223">SuperGrid</span></span>|<span data-ttu-id="ae179-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="ae179-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="ae179-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae179-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="ae179-226">Controles dos Windows Forms são expostos ao [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="ae179-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="ae179-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="ae179-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="ae179-228">Normalmente, controles de formulários do Windows que são gerenciados wrappers [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae179-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="ae179-229">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="ae179-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="ae179-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="ae179-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="ae179-231">Botão</span><span class="sxs-lookup"><span data-stu-id="ae179-231">Button</span></span>|  
|<span data-ttu-id="ae179-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ae179-232">CheckBox</span></span>|  
|<span data-ttu-id="ae179-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="ae179-233">CheckedListBox</span></span>|  
|<span data-ttu-id="ae179-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ae179-234">ColorDialog</span></span>|  
|<span data-ttu-id="ae179-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ae179-235">ComboBox</span></span>|  
|<span data-ttu-id="ae179-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="ae179-236">FolderBrowser</span></span>|  
|<span data-ttu-id="ae179-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="ae179-237">FontDialog</span></span>|  
|<span data-ttu-id="ae179-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="ae179-238">GroupBox</span></span>|  
|<span data-ttu-id="ae179-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="ae179-239">HscrollBar</span></span>|  
|<span data-ttu-id="ae179-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="ae179-240">ImageList</span></span>|  
|<span data-ttu-id="ae179-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="ae179-241">Label</span></span>|  
|<span data-ttu-id="ae179-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="ae179-242">ListBox</span></span>|  
|<span data-ttu-id="ae179-243">ListView</span><span class="sxs-lookup"><span data-stu-id="ae179-243">ListView</span></span>|  
|<span data-ttu-id="ae179-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="ae179-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="ae179-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="ae179-245">MonthCalendar</span></span>|  
|<span data-ttu-id="ae179-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="ae179-246">NotifyIcon</span></span>|  
|<span data-ttu-id="ae179-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="ae179-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="ae179-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="ae179-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="ae179-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="ae179-249">PrintDialog</span></span>|  
|<span data-ttu-id="ae179-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ae179-250">ProgressBar</span></span>|  
|<span data-ttu-id="ae179-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ae179-251">RadioButton</span></span>|  
|<span data-ttu-id="ae179-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ae179-252">RichTextBox</span></span>|  
|<span data-ttu-id="ae179-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="ae179-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="ae179-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="ae179-254">ScrollableControl</span></span>|  
|<span data-ttu-id="ae179-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="ae179-255">SoundPlayer</span></span>|  
|<span data-ttu-id="ae179-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="ae179-256">StatusBar</span></span>|  
|<span data-ttu-id="ae179-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="ae179-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="ae179-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="ae179-258">TextBox</span></span>|  
|<span data-ttu-id="ae179-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="ae179-259">Timer</span></span>|  
|<span data-ttu-id="ae179-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="ae179-260">Toolbar</span></span>|  
|<span data-ttu-id="ae179-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ae179-261">ToolTip</span></span>|  
|<span data-ttu-id="ae179-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="ae179-262">TrackBar</span></span>|  
|<span data-ttu-id="ae179-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="ae179-263">TreeView</span></span>|  
|<span data-ttu-id="ae179-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="ae179-264">VscrollBar</span></span>|  
|<span data-ttu-id="ae179-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="ae179-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="ae179-266">Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] somente através de seu suporte [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae179-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="ae179-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ae179-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="ae179-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="ae179-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="ae179-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="ae179-269">BindingSource</span></span>|  
|<span data-ttu-id="ae179-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ae179-270">DataGrid</span></span>|  
|<span data-ttu-id="ae179-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="ae179-271">DataGridView</span></span>|  
|<span data-ttu-id="ae179-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="ae179-272">DataNavigator</span></span>|  
|<span data-ttu-id="ae179-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="ae179-273">DomainUpDown</span></span>|  
|<span data-ttu-id="ae179-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="ae179-274">ErrorProvider</span></span>|  
|<span data-ttu-id="ae179-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ae179-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="ae179-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="ae179-276">Form</span></span>|  
|<span data-ttu-id="ae179-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="ae179-277">LinkLabel</span></span>|  
|<span data-ttu-id="ae179-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="ae179-278">HelpProvider</span></span>|  
|<span data-ttu-id="ae179-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="ae179-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="ae179-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="ae179-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="ae179-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="ae179-281">NumericUpDown</span></span>|  
|<span data-ttu-id="ae179-282">Painel</span><span class="sxs-lookup"><span data-stu-id="ae179-282">Panel</span></span>|  
|<span data-ttu-id="ae179-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="ae179-283">PictureBox</span></span>|  
|<span data-ttu-id="ae179-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="ae179-284">PrintDocument</span></span>|  
|<span data-ttu-id="ae179-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="ae179-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="ae179-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="ae179-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="ae179-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="ae179-287">PropertyGrid</span></span>|  
|<span data-ttu-id="ae179-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="ae179-288">UserControl</span></span>|  
|<span data-ttu-id="ae179-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ae179-289">ToolStrip</span></span>|  
|<span data-ttu-id="ae179-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ae179-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="ae179-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="ae179-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="ae179-292">Divisor</span><span class="sxs-lookup"><span data-stu-id="ae179-292">Splitter</span></span>|  
|<span data-ttu-id="ae179-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="ae179-293">RaftingContainer</span></span>|  
|<span data-ttu-id="ae179-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="ae179-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae179-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae179-295">See also</span></span>
- <span data-ttu-id="ae179-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="ae179-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)</span></span>
