---
title: "Suporte de automação de interface do usuário para Controles Padrão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f7529c68e96f93ebbba9fc5e750e09331bda9699
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="022d9-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="022d9-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="022d9-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="022d9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="022d9-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="022d9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="022d9-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] oferece suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="022d9-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="022d9-106">Controles do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="022d9-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="022d9-107">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte de interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022d9-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="022d9-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022d9-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="022d9-109">Controles de Win32</span><span class="sxs-lookup"><span data-stu-id="022d9-109">Win32 Controls</span></span>  
 <span data-ttu-id="022d9-110">A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="022d9-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="022d9-111">Esse assembly é registrado automaticamente para uso com aplicativos clientes de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="022d9-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="022d9-112">Suporte completo é fornecido somente para controles da versão 6 da Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="022d9-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="022d9-113">Há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="022d9-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="022d9-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="022d9-114">Class name</span></span>|<span data-ttu-id="022d9-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="022d9-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="022d9-116">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-116">Button</span></span>|<span data-ttu-id="022d9-117">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-117">Button</span></span>|  
|<span data-ttu-id="022d9-118">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-118">Button</span></span>|<span data-ttu-id="022d9-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="022d9-119">RadioButton</span></span>|  
|<span data-ttu-id="022d9-120">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-120">Button</span></span>|<span data-ttu-id="022d9-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="022d9-121">Group</span></span>|  
|<span data-ttu-id="022d9-122">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-122">Button</span></span>|<span data-ttu-id="022d9-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="022d9-123">CheckBox</span></span>|  
|<span data-ttu-id="022d9-124">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-124">Button</span></span>|<span data-ttu-id="022d9-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="022d9-125">Hyperlink</span></span>|  
|<span data-ttu-id="022d9-126">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-126">Button</span></span>|<span data-ttu-id="022d9-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="022d9-127">SplitButton</span></span>|  
|<span data-ttu-id="022d9-128">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-128">Button</span></span>|<span data-ttu-id="022d9-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="022d9-129">CheckBox</span></span>|  
|<span data-ttu-id="022d9-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="022d9-130">ComboBoxEx32</span></span>|<span data-ttu-id="022d9-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="022d9-131">ComboBox</span></span>|  
|<span data-ttu-id="022d9-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="022d9-132">ComboBox</span></span>|<span data-ttu-id="022d9-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="022d9-133">ComboBox</span></span>|  
|<span data-ttu-id="022d9-134">Editar</span><span class="sxs-lookup"><span data-stu-id="022d9-134">Edit</span></span>|<span data-ttu-id="022d9-135">Documento</span><span class="sxs-lookup"><span data-stu-id="022d9-135">Document</span></span>|  
|<span data-ttu-id="022d9-136">Editar</span><span class="sxs-lookup"><span data-stu-id="022d9-136">Edit</span></span>|<span data-ttu-id="022d9-137">Editar</span><span class="sxs-lookup"><span data-stu-id="022d9-137">Edit</span></span>|  
|<span data-ttu-id="022d9-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="022d9-138">SysLink</span></span>|<span data-ttu-id="022d9-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="022d9-139">Hyperlink</span></span>|  
|<span data-ttu-id="022d9-140">Estático</span><span class="sxs-lookup"><span data-stu-id="022d9-140">Static</span></span>|<span data-ttu-id="022d9-141">Texto</span><span class="sxs-lookup"><span data-stu-id="022d9-141">Text</span></span>|  
|<span data-ttu-id="022d9-142">Estático</span><span class="sxs-lookup"><span data-stu-id="022d9-142">Static</span></span>|<span data-ttu-id="022d9-143">Image</span><span class="sxs-lookup"><span data-stu-id="022d9-143">Image</span></span>|  
|<span data-ttu-id="022d9-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="022d9-144">SysIPAddress32</span></span>|<span data-ttu-id="022d9-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="022d9-145">Custom</span></span>|  
|<span data-ttu-id="022d9-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="022d9-146">SysHeader32</span></span>|<span data-ttu-id="022d9-147">Cabeçalho/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="022d9-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="022d9-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="022d9-148">SysListView32</span></span>|<span data-ttu-id="022d9-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="022d9-149">DataGrid</span></span>|  
|<span data-ttu-id="022d9-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="022d9-150">SysListView32</span></span>|<span data-ttu-id="022d9-151">Lista</span><span class="sxs-lookup"><span data-stu-id="022d9-151">List</span></span>|  
|<span data-ttu-id="022d9-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="022d9-152">ListBox</span></span>|<span data-ttu-id="022d9-153">Lista</span><span class="sxs-lookup"><span data-stu-id="022d9-153">List</span></span>|  
|<span data-ttu-id="022d9-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="022d9-154">ListBox</span></span>|<span data-ttu-id="022d9-155">Item de lista</span><span class="sxs-lookup"><span data-stu-id="022d9-155">ListItem</span></span>|  
|<span data-ttu-id="022d9-156">#32768</span><span class="sxs-lookup"><span data-stu-id="022d9-156">#32768</span></span>|<span data-ttu-id="022d9-157">Menu</span><span class="sxs-lookup"><span data-stu-id="022d9-157">Menu</span></span>|  
|<span data-ttu-id="022d9-158">#32768</span><span class="sxs-lookup"><span data-stu-id="022d9-158">#32768</span></span>|<span data-ttu-id="022d9-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="022d9-159">MenuItem</span></span>|  
|<span data-ttu-id="022d9-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="022d9-160">msctls_progress32</span></span>|<span data-ttu-id="022d9-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="022d9-161">ProgressBar</span></span>|  
|<span data-ttu-id="022d9-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="022d9-162">RichEdit</span></span>|<span data-ttu-id="022d9-163">documento.</span><span class="sxs-lookup"><span data-stu-id="022d9-163">Document.</span></span> <span data-ttu-id="022d9-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="022d9-164">See note.</span></span>|  
|<span data-ttu-id="022d9-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="022d9-165">RichEdit20A</span></span>|<span data-ttu-id="022d9-166">Documento</span><span class="sxs-lookup"><span data-stu-id="022d9-166">Document</span></span>|  
|<span data-ttu-id="022d9-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="022d9-167">RichEdit20W</span></span>|<span data-ttu-id="022d9-168">Documento</span><span class="sxs-lookup"><span data-stu-id="022d9-168">Document</span></span>|  
|<span data-ttu-id="022d9-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="022d9-169">RichEdit50W</span></span>|<span data-ttu-id="022d9-170">Documento</span><span class="sxs-lookup"><span data-stu-id="022d9-170">Document</span></span>|  
|<span data-ttu-id="022d9-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="022d9-171">ScrollBar</span></span>|<span data-ttu-id="022d9-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="022d9-172">Slider</span></span>|  
|<span data-ttu-id="022d9-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="022d9-173">msctls_trackbar32</span></span>|<span data-ttu-id="022d9-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="022d9-174">Slider</span></span>|  
|<span data-ttu-id="022d9-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="022d9-175">msctls_updown32</span></span>|<span data-ttu-id="022d9-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="022d9-176">Spinner</span></span>|  
|<span data-ttu-id="022d9-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="022d9-177">msctls_statusbar32</span></span>|<span data-ttu-id="022d9-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="022d9-178">StatusBar</span></span>|  
|<span data-ttu-id="022d9-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="022d9-179">SysTabControl32</span></span>|<span data-ttu-id="022d9-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="022d9-180">Tab</span></span>|  
|<span data-ttu-id="022d9-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="022d9-181">SysTabControl32</span></span>|<span data-ttu-id="022d9-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="022d9-182">TabItem</span></span>|  
|<span data-ttu-id="022d9-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-183">ToolbarWindow32</span></span>|<span data-ttu-id="022d9-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="022d9-184">ToolBar</span></span>|  
|<span data-ttu-id="022d9-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-185">ToolbarWindow32</span></span>|<span data-ttu-id="022d9-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="022d9-186">MenuItem</span></span>|  
|<span data-ttu-id="022d9-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-187">ToolbarWindow32</span></span>|<span data-ttu-id="022d9-188">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-188">Button</span></span>|  
|<span data-ttu-id="022d9-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-189">ToolbarWindow32</span></span>|<span data-ttu-id="022d9-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="022d9-190">CheckBox</span></span>|  
|<span data-ttu-id="022d9-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-191">ToolbarWindow32</span></span>|<span data-ttu-id="022d9-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="022d9-192">RadioButton</span></span>|  
|<span data-ttu-id="022d9-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-193">ToolbarWindow32</span></span>|<span data-ttu-id="022d9-194">Separador</span><span class="sxs-lookup"><span data-stu-id="022d9-194">Separator</span></span>|  
|<span data-ttu-id="022d9-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="022d9-195">tooltips_class32</span></span>|<span data-ttu-id="022d9-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="022d9-196">ToolTip</span></span>|  
|<span data-ttu-id="022d9-197">#32774</span><span class="sxs-lookup"><span data-stu-id="022d9-197">#32774</span></span>|<span data-ttu-id="022d9-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="022d9-198">ToolTip</span></span>|  
|<span data-ttu-id="022d9-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="022d9-199">ReBarWindow32</span></span>|<span data-ttu-id="022d9-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="022d9-200">Toolbar</span></span>|  
|<span data-ttu-id="022d9-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="022d9-201">SysTreeView32</span></span>|<span data-ttu-id="022d9-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="022d9-202">Tree</span></span>|  
|<span data-ttu-id="022d9-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="022d9-203">SysTreeView32</span></span>|<span data-ttu-id="022d9-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="022d9-204">TreeItem</span></span>|  
  
 <span data-ttu-id="022d9-205">**Observação** controle RichEdit o tem suporte apenas para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (no RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="022d9-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="022d9-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="022d9-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="022d9-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="022d9-207">Class name</span></span>|<span data-ttu-id="022d9-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="022d9-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="022d9-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="022d9-209">SysAnimate32</span></span>|<span data-ttu-id="022d9-210">Image</span><span class="sxs-lookup"><span data-stu-id="022d9-210">Image</span></span>|  
|<span data-ttu-id="022d9-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="022d9-211">SysPager</span></span>|<span data-ttu-id="022d9-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="022d9-212">Spinner</span></span>|  
|<span data-ttu-id="022d9-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="022d9-213">SysDateTimePick32</span></span>|<span data-ttu-id="022d9-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="022d9-214">Custom</span></span>|  
|<span data-ttu-id="022d9-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="022d9-215">SysMonthCal32</span></span>|<span data-ttu-id="022d9-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="022d9-216">Calendar</span></span>|  
|<span data-ttu-id="022d9-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="022d9-217">MS_WINNOTE</span></span>|<span data-ttu-id="022d9-218">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="022d9-218">Tooltip</span></span>|  
|<span data-ttu-id="022d9-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="022d9-219">VBBubble</span></span>|<span data-ttu-id="022d9-220">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="022d9-220">Tooltip</span></span>|  
|<span data-ttu-id="022d9-221">Barra de rolagem (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="022d9-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="022d9-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="022d9-222">Slider</span></span>|  
|<span data-ttu-id="022d9-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="022d9-223">SuperGrid</span></span>|<span data-ttu-id="022d9-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="022d9-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="022d9-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="022d9-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="022d9-226">controles são expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="022d9-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="022d9-227">Esse assembly é registrado automaticamente para uso com aplicativos clientes de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="022d9-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="022d9-228">Normalmente, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controles que são gerenciados wrappers para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022d9-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="022d9-229">Há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="022d9-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="022d9-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="022d9-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="022d9-231">Botão</span><span class="sxs-lookup"><span data-stu-id="022d9-231">Button</span></span>|  
|<span data-ttu-id="022d9-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="022d9-232">CheckBox</span></span>|  
|<span data-ttu-id="022d9-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="022d9-233">CheckedListBox</span></span>|  
|<span data-ttu-id="022d9-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="022d9-234">ColorDialog</span></span>|  
|<span data-ttu-id="022d9-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="022d9-235">ComboBox</span></span>|  
|<span data-ttu-id="022d9-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="022d9-236">FolderBrowser</span></span>|  
|<span data-ttu-id="022d9-237">FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="022d9-237">FontDialog</span></span>|  
|<span data-ttu-id="022d9-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="022d9-238">GroupBox</span></span>|  
|<span data-ttu-id="022d9-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="022d9-239">HscrollBar</span></span>|  
|<span data-ttu-id="022d9-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="022d9-240">ImageList</span></span>|  
|<span data-ttu-id="022d9-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="022d9-241">Label</span></span>|  
|<span data-ttu-id="022d9-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="022d9-242">ListBox</span></span>|  
|<span data-ttu-id="022d9-243">ListView</span><span class="sxs-lookup"><span data-stu-id="022d9-243">ListView</span></span>|  
|<span data-ttu-id="022d9-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="022d9-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="022d9-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="022d9-245">MonthCalendar</span></span>|  
|<span data-ttu-id="022d9-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="022d9-246">NotifyIcon</span></span>|  
|<span data-ttu-id="022d9-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="022d9-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="022d9-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="022d9-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="022d9-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="022d9-249">PrintDialog</span></span>|  
|<span data-ttu-id="022d9-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="022d9-250">ProgressBar</span></span>|  
|<span data-ttu-id="022d9-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="022d9-251">RadioButton</span></span>|  
|<span data-ttu-id="022d9-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="022d9-252">RichTextBox</span></span>|  
|<span data-ttu-id="022d9-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="022d9-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="022d9-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="022d9-254">ScrollableControl</span></span>|  
|<span data-ttu-id="022d9-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="022d9-255">SoundPlayer</span></span>|  
|<span data-ttu-id="022d9-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="022d9-256">StatusBar</span></span>|  
|<span data-ttu-id="022d9-257">TabPage/TabControl</span><span class="sxs-lookup"><span data-stu-id="022d9-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="022d9-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="022d9-258">TextBox</span></span>|  
|<span data-ttu-id="022d9-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="022d9-259">Timer</span></span>|  
|<span data-ttu-id="022d9-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="022d9-260">Toolbar</span></span>|  
|<span data-ttu-id="022d9-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="022d9-261">ToolTip</span></span>|  
|<span data-ttu-id="022d9-262">Barra de controle</span><span class="sxs-lookup"><span data-stu-id="022d9-262">TrackBar</span></span>|  
|<span data-ttu-id="022d9-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="022d9-263">TreeView</span></span>|  
|<span data-ttu-id="022d9-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="022d9-264">VscrollBar</span></span>|  
|<span data-ttu-id="022d9-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="022d9-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="022d9-266">Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas através de seu suporte para [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="022d9-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="022d9-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="022d9-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="022d9-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="022d9-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="022d9-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="022d9-269">BindingSource</span></span>|  
|<span data-ttu-id="022d9-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="022d9-270">DataGrid</span></span>|  
|<span data-ttu-id="022d9-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="022d9-271">DataGridView</span></span>|  
|<span data-ttu-id="022d9-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="022d9-272">DataNavigator</span></span>|  
|<span data-ttu-id="022d9-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="022d9-273">DomainUpDown</span></span>|  
|<span data-ttu-id="022d9-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="022d9-274">ErrorProvider</span></span>|  
|<span data-ttu-id="022d9-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="022d9-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="022d9-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="022d9-276">Form</span></span>|  
|<span data-ttu-id="022d9-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="022d9-277">LinkLabel</span></span>|  
|<span data-ttu-id="022d9-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="022d9-278">HelpProvider</span></span>|  
|<span data-ttu-id="022d9-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="022d9-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="022d9-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="022d9-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="022d9-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="022d9-281">NumericUpDown</span></span>|  
|<span data-ttu-id="022d9-282">Painel</span><span class="sxs-lookup"><span data-stu-id="022d9-282">Panel</span></span>|  
|<span data-ttu-id="022d9-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="022d9-283">PictureBox</span></span>|  
|<span data-ttu-id="022d9-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="022d9-284">PrintDocument</span></span>|  
|<span data-ttu-id="022d9-285">Controle PrintPreview</span><span class="sxs-lookup"><span data-stu-id="022d9-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="022d9-286">Caixa de diálogo PrintPreview</span><span class="sxs-lookup"><span data-stu-id="022d9-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="022d9-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="022d9-287">PropertyGrid</span></span>|  
|<span data-ttu-id="022d9-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="022d9-288">UserControl</span></span>|  
|<span data-ttu-id="022d9-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="022d9-289">ToolStrip</span></span>|  
|<span data-ttu-id="022d9-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="022d9-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="022d9-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="022d9-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="022d9-292">Separador</span><span class="sxs-lookup"><span data-stu-id="022d9-292">Splitter</span></span>|  
|<span data-ttu-id="022d9-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="022d9-293">RaftingContainer</span></span>|  
|<span data-ttu-id="022d9-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="022d9-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="022d9-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="022d9-295">See Also</span></span>  
 <span data-ttu-id="022d9-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="022d9-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)</span></span>
