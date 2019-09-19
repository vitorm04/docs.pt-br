---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042005"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="d0059-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="d0059-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="d0059-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d0059-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d0059-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d0059-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d0059-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o suporte para controles padrão em aplicativos desenvolvidos para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]as [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]estruturas do [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] , e.</span><span class="sxs-lookup"><span data-stu-id="d0059-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="d0059-106">Controles de Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d0059-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="d0059-107">Todos [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] os elementos de controle que fornecem informações ou suporte para interação do usuário têm suporte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nativo completo para o.</span><span class="sxs-lookup"><span data-stu-id="d0059-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d0059-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0059-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="d0059-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="d0059-109">Win32 Controls</span></span>  
 <span data-ttu-id="d0059-110">A [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] maioria dos controles é [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] exposta a provedores do lado do cliente em UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="d0059-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d0059-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d0059-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d0059-112">O suporte completo é fornecido somente para controles da versão 6 do ComCtrl32. dll (disponível [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] com e posterior).</span><span class="sxs-lookup"><span data-stu-id="d0059-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="d0059-113">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="d0059-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d0059-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="d0059-114">Class name</span></span>|<span data-ttu-id="d0059-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="d0059-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d0059-116">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-116">Button</span></span>|<span data-ttu-id="d0059-117">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-117">Button</span></span>|  
|<span data-ttu-id="d0059-118">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-118">Button</span></span>|<span data-ttu-id="d0059-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d0059-119">RadioButton</span></span>|  
|<span data-ttu-id="d0059-120">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-120">Button</span></span>|<span data-ttu-id="d0059-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="d0059-121">Group</span></span>|  
|<span data-ttu-id="d0059-122">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-122">Button</span></span>|<span data-ttu-id="d0059-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d0059-123">CheckBox</span></span>|  
|<span data-ttu-id="d0059-124">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-124">Button</span></span>|<span data-ttu-id="d0059-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="d0059-125">Hyperlink</span></span>|  
|<span data-ttu-id="d0059-126">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-126">Button</span></span>|<span data-ttu-id="d0059-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="d0059-127">SplitButton</span></span>|  
|<span data-ttu-id="d0059-128">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-128">Button</span></span>|<span data-ttu-id="d0059-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d0059-129">CheckBox</span></span>|  
|<span data-ttu-id="d0059-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="d0059-130">ComboBoxEx32</span></span>|<span data-ttu-id="d0059-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d0059-131">ComboBox</span></span>|  
|<span data-ttu-id="d0059-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d0059-132">ComboBox</span></span>|<span data-ttu-id="d0059-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d0059-133">ComboBox</span></span>|  
|<span data-ttu-id="d0059-134">Editar</span><span class="sxs-lookup"><span data-stu-id="d0059-134">Edit</span></span>|<span data-ttu-id="d0059-135">Documento</span><span class="sxs-lookup"><span data-stu-id="d0059-135">Document</span></span>|  
|<span data-ttu-id="d0059-136">Editar</span><span class="sxs-lookup"><span data-stu-id="d0059-136">Edit</span></span>|<span data-ttu-id="d0059-137">Editar</span><span class="sxs-lookup"><span data-stu-id="d0059-137">Edit</span></span>|  
|<span data-ttu-id="d0059-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="d0059-138">SysLink</span></span>|<span data-ttu-id="d0059-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="d0059-139">Hyperlink</span></span>|  
|<span data-ttu-id="d0059-140">Estático</span><span class="sxs-lookup"><span data-stu-id="d0059-140">Static</span></span>|<span data-ttu-id="d0059-141">Texto</span><span class="sxs-lookup"><span data-stu-id="d0059-141">Text</span></span>|  
|<span data-ttu-id="d0059-142">Estático</span><span class="sxs-lookup"><span data-stu-id="d0059-142">Static</span></span>|<span data-ttu-id="d0059-143">Image</span><span class="sxs-lookup"><span data-stu-id="d0059-143">Image</span></span>|  
|<span data-ttu-id="d0059-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="d0059-144">SysIPAddress32</span></span>|<span data-ttu-id="d0059-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="d0059-145">Custom</span></span>|  
|<span data-ttu-id="d0059-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="d0059-146">SysHeader32</span></span>|<span data-ttu-id="d0059-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="d0059-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="d0059-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d0059-148">SysListView32</span></span>|<span data-ttu-id="d0059-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d0059-149">DataGrid</span></span>|  
|<span data-ttu-id="d0059-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d0059-150">SysListView32</span></span>|<span data-ttu-id="d0059-151">Lista</span><span class="sxs-lookup"><span data-stu-id="d0059-151">List</span></span>|  
|<span data-ttu-id="d0059-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="d0059-152">ListBox</span></span>|<span data-ttu-id="d0059-153">Lista</span><span class="sxs-lookup"><span data-stu-id="d0059-153">List</span></span>|  
|<span data-ttu-id="d0059-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="d0059-154">ListBox</span></span>|<span data-ttu-id="d0059-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="d0059-155">ListItem</span></span>|  
|<span data-ttu-id="d0059-156">#32768</span><span class="sxs-lookup"><span data-stu-id="d0059-156">#32768</span></span>|<span data-ttu-id="d0059-157">Menu</span><span class="sxs-lookup"><span data-stu-id="d0059-157">Menu</span></span>|  
|<span data-ttu-id="d0059-158">#32768</span><span class="sxs-lookup"><span data-stu-id="d0059-158">#32768</span></span>|<span data-ttu-id="d0059-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d0059-159">MenuItem</span></span>|  
|<span data-ttu-id="d0059-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="d0059-160">msctls_progress32</span></span>|<span data-ttu-id="d0059-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d0059-161">ProgressBar</span></span>|  
|<span data-ttu-id="d0059-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="d0059-162">RichEdit</span></span>|<span data-ttu-id="d0059-163">Document.</span><span class="sxs-lookup"><span data-stu-id="d0059-163">Document.</span></span> <span data-ttu-id="d0059-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="d0059-164">See note.</span></span>|  
|<span data-ttu-id="d0059-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="d0059-165">RichEdit20A</span></span>|<span data-ttu-id="d0059-166">Documento</span><span class="sxs-lookup"><span data-stu-id="d0059-166">Document</span></span>|  
|<span data-ttu-id="d0059-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="d0059-167">RichEdit20W</span></span>|<span data-ttu-id="d0059-168">Documento</span><span class="sxs-lookup"><span data-stu-id="d0059-168">Document</span></span>|  
|<span data-ttu-id="d0059-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="d0059-169">RichEdit50W</span></span>|<span data-ttu-id="d0059-170">Documento</span><span class="sxs-lookup"><span data-stu-id="d0059-170">Document</span></span>|  
|<span data-ttu-id="d0059-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="d0059-171">ScrollBar</span></span>|<span data-ttu-id="d0059-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="d0059-172">Slider</span></span>|  
|<span data-ttu-id="d0059-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="d0059-173">msctls_trackbar32</span></span>|<span data-ttu-id="d0059-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="d0059-174">Slider</span></span>|  
|<span data-ttu-id="d0059-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="d0059-175">msctls_updown32</span></span>|<span data-ttu-id="d0059-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="d0059-176">Spinner</span></span>|  
|<span data-ttu-id="d0059-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="d0059-177">msctls_statusbar32</span></span>|<span data-ttu-id="d0059-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d0059-178">StatusBar</span></span>|  
|<span data-ttu-id="d0059-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d0059-179">SysTabControl32</span></span>|<span data-ttu-id="d0059-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="d0059-180">Tab</span></span>|  
|<span data-ttu-id="d0059-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d0059-181">SysTabControl32</span></span>|<span data-ttu-id="d0059-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="d0059-182">TabItem</span></span>|  
|<span data-ttu-id="d0059-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-183">ToolbarWindow32</span></span>|<span data-ttu-id="d0059-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="d0059-184">ToolBar</span></span>|  
|<span data-ttu-id="d0059-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-185">ToolbarWindow32</span></span>|<span data-ttu-id="d0059-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d0059-186">MenuItem</span></span>|  
|<span data-ttu-id="d0059-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-187">ToolbarWindow32</span></span>|<span data-ttu-id="d0059-188">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-188">Button</span></span>|  
|<span data-ttu-id="d0059-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-189">ToolbarWindow32</span></span>|<span data-ttu-id="d0059-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d0059-190">CheckBox</span></span>|  
|<span data-ttu-id="d0059-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-191">ToolbarWindow32</span></span>|<span data-ttu-id="d0059-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d0059-192">RadioButton</span></span>|  
|<span data-ttu-id="d0059-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-193">ToolbarWindow32</span></span>|<span data-ttu-id="d0059-194">Separador</span><span class="sxs-lookup"><span data-stu-id="d0059-194">Separator</span></span>|  
|<span data-ttu-id="d0059-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="d0059-195">tooltips_class32</span></span>|<span data-ttu-id="d0059-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d0059-196">ToolTip</span></span>|  
|<span data-ttu-id="d0059-197">#32774</span><span class="sxs-lookup"><span data-stu-id="d0059-197">#32774</span></span>|<span data-ttu-id="d0059-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d0059-198">ToolTip</span></span>|  
|<span data-ttu-id="d0059-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="d0059-199">ReBarWindow32</span></span>|<span data-ttu-id="d0059-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="d0059-200">Toolbar</span></span>|  
|<span data-ttu-id="d0059-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d0059-201">SysTreeView32</span></span>|<span data-ttu-id="d0059-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="d0059-202">Tree</span></span>|  
|<span data-ttu-id="d0059-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d0059-203">SysTreeView32</span></span>|<span data-ttu-id="d0059-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="d0059-204">TreeItem</span></span>|  
  
 <span data-ttu-id="d0059-205">**Observação** O controle RichEdit tem suporte apenas para as versões fornecidas [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] com (em Riched20. dll versão 3,1 e posterior e MsftEdit. dll versão 4,1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="d0059-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="d0059-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="d0059-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="d0059-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="d0059-207">Class name</span></span>|<span data-ttu-id="d0059-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="d0059-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d0059-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="d0059-209">SysAnimate32</span></span>|<span data-ttu-id="d0059-210">Image</span><span class="sxs-lookup"><span data-stu-id="d0059-210">Image</span></span>|  
|<span data-ttu-id="d0059-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="d0059-211">SysPager</span></span>|<span data-ttu-id="d0059-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="d0059-212">Spinner</span></span>|  
|<span data-ttu-id="d0059-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="d0059-213">SysDateTimePick32</span></span>|<span data-ttu-id="d0059-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="d0059-214">Custom</span></span>|  
|<span data-ttu-id="d0059-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="d0059-215">SysMonthCal32</span></span>|<span data-ttu-id="d0059-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="d0059-216">Calendar</span></span>|  
|<span data-ttu-id="d0059-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="d0059-217">MS_WINNOTE</span></span>|<span data-ttu-id="d0059-218">Dessa</span><span class="sxs-lookup"><span data-stu-id="d0059-218">Tooltip</span></span>|  
|<span data-ttu-id="d0059-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="d0059-219">VBBubble</span></span>|<span data-ttu-id="d0059-220">Dessa</span><span class="sxs-lookup"><span data-stu-id="d0059-220">Tooltip</span></span>|  
|<span data-ttu-id="d0059-221">ScrollBar (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="d0059-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="d0059-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="d0059-222">Slider</span></span>|  
|<span data-ttu-id="d0059-223">Subgrade</span><span class="sxs-lookup"><span data-stu-id="d0059-223">SuperGrid</span></span>|<span data-ttu-id="d0059-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="d0059-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="d0059-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0059-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="d0059-226">Os controles de Windows Forms são [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expostos a por meio de provedores do lado do cliente em UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="d0059-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d0059-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d0059-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d0059-228">Normalmente, Windows Forms controles que são wrappers gerenciados [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] para controles comuns são suportados [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pelo.</span><span class="sxs-lookup"><span data-stu-id="d0059-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d0059-229">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="d0059-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d0059-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="d0059-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="d0059-231">Botão</span><span class="sxs-lookup"><span data-stu-id="d0059-231">Button</span></span>|  
|<span data-ttu-id="d0059-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d0059-232">CheckBox</span></span>|  
|<span data-ttu-id="d0059-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d0059-233">CheckedListBox</span></span>|  
|<span data-ttu-id="d0059-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d0059-234">ColorDialog</span></span>|  
|<span data-ttu-id="d0059-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d0059-235">ComboBox</span></span>|  
|<span data-ttu-id="d0059-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="d0059-236">FolderBrowser</span></span>|  
|<span data-ttu-id="d0059-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="d0059-237">FontDialog</span></span>|  
|<span data-ttu-id="d0059-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="d0059-238">GroupBox</span></span>|  
|<span data-ttu-id="d0059-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="d0059-239">HscrollBar</span></span>|  
|<span data-ttu-id="d0059-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="d0059-240">ImageList</span></span>|  
|<span data-ttu-id="d0059-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="d0059-241">Label</span></span>|  
|<span data-ttu-id="d0059-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="d0059-242">ListBox</span></span>|  
|<span data-ttu-id="d0059-243">ListView</span><span class="sxs-lookup"><span data-stu-id="d0059-243">ListView</span></span>|  
|<span data-ttu-id="d0059-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d0059-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="d0059-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d0059-245">MonthCalendar</span></span>|  
|<span data-ttu-id="d0059-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="d0059-246">NotifyIcon</span></span>|  
|<span data-ttu-id="d0059-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d0059-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="d0059-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="d0059-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="d0059-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d0059-249">PrintDialog</span></span>|  
|<span data-ttu-id="d0059-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d0059-250">ProgressBar</span></span>|  
|<span data-ttu-id="d0059-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d0059-251">RadioButton</span></span>|  
|<span data-ttu-id="d0059-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d0059-252">RichTextBox</span></span>|  
|<span data-ttu-id="d0059-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="d0059-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="d0059-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="d0059-254">ScrollableControl</span></span>|  
|<span data-ttu-id="d0059-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="d0059-255">SoundPlayer</span></span>|  
|<span data-ttu-id="d0059-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d0059-256">StatusBar</span></span>|  
|<span data-ttu-id="d0059-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="d0059-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="d0059-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="d0059-258">TextBox</span></span>|  
|<span data-ttu-id="d0059-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="d0059-259">Timer</span></span>|  
|<span data-ttu-id="d0059-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="d0059-260">Toolbar</span></span>|  
|<span data-ttu-id="d0059-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d0059-261">ToolTip</span></span>|  
|<span data-ttu-id="d0059-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="d0059-262">TrackBar</span></span>|  
|<span data-ttu-id="d0059-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="d0059-263">TreeView</span></span>|  
|<span data-ttu-id="d0059-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="d0059-264">VscrollBar</span></span>|  
|<span data-ttu-id="d0059-265">Controlo</span><span class="sxs-lookup"><span data-stu-id="d0059-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="d0059-266">Os controles a seguir são expostos [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas por meio de seu suporte para o Microsoft acessibilidade ativa.</span><span class="sxs-lookup"><span data-stu-id="d0059-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="d0059-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d0059-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="d0059-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="d0059-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="d0059-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="d0059-269">BindingSource</span></span>|  
|<span data-ttu-id="d0059-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d0059-270">DataGrid</span></span>|  
|<span data-ttu-id="d0059-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="d0059-271">DataGridView</span></span>|  
|<span data-ttu-id="d0059-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="d0059-272">DataNavigator</span></span>|  
|<span data-ttu-id="d0059-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="d0059-273">DomainUpDown</span></span>|  
|<span data-ttu-id="d0059-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="d0059-274">ErrorProvider</span></span>|  
|<span data-ttu-id="d0059-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d0059-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="d0059-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="d0059-276">Form</span></span>|  
|<span data-ttu-id="d0059-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="d0059-277">LinkLabel</span></span>|  
|<span data-ttu-id="d0059-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="d0059-278">HelpProvider</span></span>|  
|<span data-ttu-id="d0059-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d0059-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="d0059-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="d0059-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="d0059-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="d0059-281">NumericUpDown</span></span>|  
|<span data-ttu-id="d0059-282">Painel</span><span class="sxs-lookup"><span data-stu-id="d0059-282">Panel</span></span>|  
|<span data-ttu-id="d0059-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="d0059-283">PictureBox</span></span>|  
|<span data-ttu-id="d0059-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="d0059-284">PrintDocument</span></span>|  
|<span data-ttu-id="d0059-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="d0059-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="d0059-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="d0059-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="d0059-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="d0059-287">PropertyGrid</span></span>|  
|<span data-ttu-id="d0059-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="d0059-288">UserControl</span></span>|  
|<span data-ttu-id="d0059-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d0059-289">ToolStrip</span></span>|  
|<span data-ttu-id="d0059-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d0059-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="d0059-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="d0059-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="d0059-292">Divisor</span><span class="sxs-lookup"><span data-stu-id="d0059-292">Splitter</span></span>|  
|<span data-ttu-id="d0059-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="d0059-293">RaftingContainer</span></span>|  
|<span data-ttu-id="d0059-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="d0059-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0059-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0059-295">See also</span></span>

- <span data-ttu-id="d0059-296">[UI Automation Control Types](ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="d0059-296">[UI Automation Control Types](ui-automation-control-types.md)</span></span>
