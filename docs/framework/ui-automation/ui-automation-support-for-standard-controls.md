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
ms.openlocfilehash: 71a5a2e4319debf1a4d8ddd08d7f0979443682b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="56b8b-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="56b8b-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="56b8b-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="56b8b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="56b8b-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="56b8b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="56b8b-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] oferece suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="56b8b-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="56b8b-106">Controles do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="56b8b-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="56b8b-107">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte de interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b8b-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="56b8b-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b8b-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="56b8b-109">Controles de Win32</span><span class="sxs-lookup"><span data-stu-id="56b8b-109">Win32 Controls</span></span>  
 <span data-ttu-id="56b8b-110">A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="56b8b-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="56b8b-111">Esse assembly é registrado automaticamente para uso com aplicativos clientes de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="56b8b-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="56b8b-112">Suporte completo é fornecido somente para controles da versão 6 da Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="56b8b-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="56b8b-113">Há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="56b8b-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="56b8b-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="56b8b-114">Class name</span></span>|<span data-ttu-id="56b8b-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="56b8b-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="56b8b-116">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-116">Button</span></span>|<span data-ttu-id="56b8b-117">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-117">Button</span></span>|  
|<span data-ttu-id="56b8b-118">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-118">Button</span></span>|<span data-ttu-id="56b8b-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="56b8b-119">RadioButton</span></span>|  
|<span data-ttu-id="56b8b-120">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-120">Button</span></span>|<span data-ttu-id="56b8b-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="56b8b-121">Group</span></span>|  
|<span data-ttu-id="56b8b-122">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-122">Button</span></span>|<span data-ttu-id="56b8b-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-123">CheckBox</span></span>|  
|<span data-ttu-id="56b8b-124">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-124">Button</span></span>|<span data-ttu-id="56b8b-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="56b8b-125">Hyperlink</span></span>|  
|<span data-ttu-id="56b8b-126">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-126">Button</span></span>|<span data-ttu-id="56b8b-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="56b8b-127">SplitButton</span></span>|  
|<span data-ttu-id="56b8b-128">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-128">Button</span></span>|<span data-ttu-id="56b8b-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-129">CheckBox</span></span>|  
|<span data-ttu-id="56b8b-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="56b8b-130">ComboBoxEx32</span></span>|<span data-ttu-id="56b8b-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-131">ComboBox</span></span>|  
|<span data-ttu-id="56b8b-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-132">ComboBox</span></span>|<span data-ttu-id="56b8b-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-133">ComboBox</span></span>|  
|<span data-ttu-id="56b8b-134">Editar</span><span class="sxs-lookup"><span data-stu-id="56b8b-134">Edit</span></span>|<span data-ttu-id="56b8b-135">Documento</span><span class="sxs-lookup"><span data-stu-id="56b8b-135">Document</span></span>|  
|<span data-ttu-id="56b8b-136">Editar</span><span class="sxs-lookup"><span data-stu-id="56b8b-136">Edit</span></span>|<span data-ttu-id="56b8b-137">Editar</span><span class="sxs-lookup"><span data-stu-id="56b8b-137">Edit</span></span>|  
|<span data-ttu-id="56b8b-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="56b8b-138">SysLink</span></span>|<span data-ttu-id="56b8b-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="56b8b-139">Hyperlink</span></span>|  
|<span data-ttu-id="56b8b-140">Estático</span><span class="sxs-lookup"><span data-stu-id="56b8b-140">Static</span></span>|<span data-ttu-id="56b8b-141">Texto</span><span class="sxs-lookup"><span data-stu-id="56b8b-141">Text</span></span>|  
|<span data-ttu-id="56b8b-142">Estático</span><span class="sxs-lookup"><span data-stu-id="56b8b-142">Static</span></span>|<span data-ttu-id="56b8b-143">Image</span><span class="sxs-lookup"><span data-stu-id="56b8b-143">Image</span></span>|  
|<span data-ttu-id="56b8b-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="56b8b-144">SysIPAddress32</span></span>|<span data-ttu-id="56b8b-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="56b8b-145">Custom</span></span>|  
|<span data-ttu-id="56b8b-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="56b8b-146">SysHeader32</span></span>|<span data-ttu-id="56b8b-147">Cabeçalho/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="56b8b-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="56b8b-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="56b8b-148">SysListView32</span></span>|<span data-ttu-id="56b8b-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="56b8b-149">DataGrid</span></span>|  
|<span data-ttu-id="56b8b-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="56b8b-150">SysListView32</span></span>|<span data-ttu-id="56b8b-151">Lista</span><span class="sxs-lookup"><span data-stu-id="56b8b-151">List</span></span>|  
|<span data-ttu-id="56b8b-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-152">ListBox</span></span>|<span data-ttu-id="56b8b-153">Lista</span><span class="sxs-lookup"><span data-stu-id="56b8b-153">List</span></span>|  
|<span data-ttu-id="56b8b-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-154">ListBox</span></span>|<span data-ttu-id="56b8b-155">Item de lista</span><span class="sxs-lookup"><span data-stu-id="56b8b-155">ListItem</span></span>|  
|<span data-ttu-id="56b8b-156">#32768</span><span class="sxs-lookup"><span data-stu-id="56b8b-156">#32768</span></span>|<span data-ttu-id="56b8b-157">Menu</span><span class="sxs-lookup"><span data-stu-id="56b8b-157">Menu</span></span>|  
|<span data-ttu-id="56b8b-158">#32768</span><span class="sxs-lookup"><span data-stu-id="56b8b-158">#32768</span></span>|<span data-ttu-id="56b8b-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="56b8b-159">MenuItem</span></span>|  
|<span data-ttu-id="56b8b-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="56b8b-160">msctls_progress32</span></span>|<span data-ttu-id="56b8b-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-161">ProgressBar</span></span>|  
|<span data-ttu-id="56b8b-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="56b8b-162">RichEdit</span></span>|<span data-ttu-id="56b8b-163">documento.</span><span class="sxs-lookup"><span data-stu-id="56b8b-163">Document.</span></span> <span data-ttu-id="56b8b-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="56b8b-164">See note.</span></span>|  
|<span data-ttu-id="56b8b-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="56b8b-165">RichEdit20A</span></span>|<span data-ttu-id="56b8b-166">Documento</span><span class="sxs-lookup"><span data-stu-id="56b8b-166">Document</span></span>|  
|<span data-ttu-id="56b8b-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="56b8b-167">RichEdit20W</span></span>|<span data-ttu-id="56b8b-168">Documento</span><span class="sxs-lookup"><span data-stu-id="56b8b-168">Document</span></span>|  
|<span data-ttu-id="56b8b-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="56b8b-169">RichEdit50W</span></span>|<span data-ttu-id="56b8b-170">Documento</span><span class="sxs-lookup"><span data-stu-id="56b8b-170">Document</span></span>|  
|<span data-ttu-id="56b8b-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-171">ScrollBar</span></span>|<span data-ttu-id="56b8b-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="56b8b-172">Slider</span></span>|  
|<span data-ttu-id="56b8b-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="56b8b-173">msctls_trackbar32</span></span>|<span data-ttu-id="56b8b-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="56b8b-174">Slider</span></span>|  
|<span data-ttu-id="56b8b-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="56b8b-175">msctls_updown32</span></span>|<span data-ttu-id="56b8b-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="56b8b-176">Spinner</span></span>|  
|<span data-ttu-id="56b8b-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="56b8b-177">msctls_statusbar32</span></span>|<span data-ttu-id="56b8b-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-178">StatusBar</span></span>|  
|<span data-ttu-id="56b8b-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="56b8b-179">SysTabControl32</span></span>|<span data-ttu-id="56b8b-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="56b8b-180">Tab</span></span>|  
|<span data-ttu-id="56b8b-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="56b8b-181">SysTabControl32</span></span>|<span data-ttu-id="56b8b-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="56b8b-182">TabItem</span></span>|  
|<span data-ttu-id="56b8b-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-183">ToolbarWindow32</span></span>|<span data-ttu-id="56b8b-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-184">ToolBar</span></span>|  
|<span data-ttu-id="56b8b-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-185">ToolbarWindow32</span></span>|<span data-ttu-id="56b8b-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="56b8b-186">MenuItem</span></span>|  
|<span data-ttu-id="56b8b-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-187">ToolbarWindow32</span></span>|<span data-ttu-id="56b8b-188">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-188">Button</span></span>|  
|<span data-ttu-id="56b8b-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-189">ToolbarWindow32</span></span>|<span data-ttu-id="56b8b-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-190">CheckBox</span></span>|  
|<span data-ttu-id="56b8b-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-191">ToolbarWindow32</span></span>|<span data-ttu-id="56b8b-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="56b8b-192">RadioButton</span></span>|  
|<span data-ttu-id="56b8b-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-193">ToolbarWindow32</span></span>|<span data-ttu-id="56b8b-194">Separador</span><span class="sxs-lookup"><span data-stu-id="56b8b-194">Separator</span></span>|  
|<span data-ttu-id="56b8b-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="56b8b-195">tooltips_class32</span></span>|<span data-ttu-id="56b8b-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="56b8b-196">ToolTip</span></span>|  
|<span data-ttu-id="56b8b-197">#32774</span><span class="sxs-lookup"><span data-stu-id="56b8b-197">#32774</span></span>|<span data-ttu-id="56b8b-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="56b8b-198">ToolTip</span></span>|  
|<span data-ttu-id="56b8b-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="56b8b-199">ReBarWindow32</span></span>|<span data-ttu-id="56b8b-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="56b8b-200">Toolbar</span></span>|  
|<span data-ttu-id="56b8b-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="56b8b-201">SysTreeView32</span></span>|<span data-ttu-id="56b8b-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="56b8b-202">Tree</span></span>|  
|<span data-ttu-id="56b8b-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="56b8b-203">SysTreeView32</span></span>|<span data-ttu-id="56b8b-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="56b8b-204">TreeItem</span></span>|  
  
 <span data-ttu-id="56b8b-205">**Observação** controle RichEdit o tem suporte apenas para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (no RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="56b8b-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="56b8b-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="56b8b-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="56b8b-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="56b8b-207">Class name</span></span>|<span data-ttu-id="56b8b-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="56b8b-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="56b8b-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="56b8b-209">SysAnimate32</span></span>|<span data-ttu-id="56b8b-210">Image</span><span class="sxs-lookup"><span data-stu-id="56b8b-210">Image</span></span>|  
|<span data-ttu-id="56b8b-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="56b8b-211">SysPager</span></span>|<span data-ttu-id="56b8b-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="56b8b-212">Spinner</span></span>|  
|<span data-ttu-id="56b8b-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="56b8b-213">SysDateTimePick32</span></span>|<span data-ttu-id="56b8b-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="56b8b-214">Custom</span></span>|  
|<span data-ttu-id="56b8b-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="56b8b-215">SysMonthCal32</span></span>|<span data-ttu-id="56b8b-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="56b8b-216">Calendar</span></span>|  
|<span data-ttu-id="56b8b-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="56b8b-217">MS_WINNOTE</span></span>|<span data-ttu-id="56b8b-218">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="56b8b-218">Tooltip</span></span>|  
|<span data-ttu-id="56b8b-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="56b8b-219">VBBubble</span></span>|<span data-ttu-id="56b8b-220">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="56b8b-220">Tooltip</span></span>|  
|<span data-ttu-id="56b8b-221">Barra de rolagem (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="56b8b-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="56b8b-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="56b8b-222">Slider</span></span>|  
|<span data-ttu-id="56b8b-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="56b8b-223">SuperGrid</span></span>|<span data-ttu-id="56b8b-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="56b8b-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="56b8b-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56b8b-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="56b8b-226">controles são expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="56b8b-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="56b8b-227">Esse assembly é registrado automaticamente para uso com aplicativos clientes de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="56b8b-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="56b8b-228">Normalmente, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controles que são gerenciados wrappers para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b8b-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="56b8b-229">Há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="56b8b-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="56b8b-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="56b8b-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="56b8b-231">Botão</span><span class="sxs-lookup"><span data-stu-id="56b8b-231">Button</span></span>|  
|<span data-ttu-id="56b8b-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-232">CheckBox</span></span>|  
|<span data-ttu-id="56b8b-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-233">CheckedListBox</span></span>|  
|<span data-ttu-id="56b8b-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="56b8b-234">ColorDialog</span></span>|  
|<span data-ttu-id="56b8b-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-235">ComboBox</span></span>|  
|<span data-ttu-id="56b8b-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="56b8b-236">FolderBrowser</span></span>|  
|<span data-ttu-id="56b8b-237">FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="56b8b-237">FontDialog</span></span>|  
|<span data-ttu-id="56b8b-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-238">GroupBox</span></span>|  
|<span data-ttu-id="56b8b-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-239">HscrollBar</span></span>|  
|<span data-ttu-id="56b8b-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="56b8b-240">ImageList</span></span>|  
|<span data-ttu-id="56b8b-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="56b8b-241">Label</span></span>|  
|<span data-ttu-id="56b8b-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-242">ListBox</span></span>|  
|<span data-ttu-id="56b8b-243">ListView</span><span class="sxs-lookup"><span data-stu-id="56b8b-243">ListView</span></span>|  
|<span data-ttu-id="56b8b-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="56b8b-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="56b8b-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="56b8b-245">MonthCalendar</span></span>|  
|<span data-ttu-id="56b8b-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="56b8b-246">NotifyIcon</span></span>|  
|<span data-ttu-id="56b8b-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="56b8b-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="56b8b-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="56b8b-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="56b8b-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="56b8b-249">PrintDialog</span></span>|  
|<span data-ttu-id="56b8b-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-250">ProgressBar</span></span>|  
|<span data-ttu-id="56b8b-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="56b8b-251">RadioButton</span></span>|  
|<span data-ttu-id="56b8b-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-252">RichTextBox</span></span>|  
|<span data-ttu-id="56b8b-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="56b8b-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="56b8b-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="56b8b-254">ScrollableControl</span></span>|  
|<span data-ttu-id="56b8b-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="56b8b-255">SoundPlayer</span></span>|  
|<span data-ttu-id="56b8b-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-256">StatusBar</span></span>|  
|<span data-ttu-id="56b8b-257">TabPage/TabControl</span><span class="sxs-lookup"><span data-stu-id="56b8b-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="56b8b-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-258">TextBox</span></span>|  
|<span data-ttu-id="56b8b-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="56b8b-259">Timer</span></span>|  
|<span data-ttu-id="56b8b-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="56b8b-260">Toolbar</span></span>|  
|<span data-ttu-id="56b8b-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="56b8b-261">ToolTip</span></span>|  
|<span data-ttu-id="56b8b-262">Barra de controle</span><span class="sxs-lookup"><span data-stu-id="56b8b-262">TrackBar</span></span>|  
|<span data-ttu-id="56b8b-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="56b8b-263">TreeView</span></span>|  
|<span data-ttu-id="56b8b-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="56b8b-264">VscrollBar</span></span>|  
|<span data-ttu-id="56b8b-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="56b8b-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="56b8b-266">Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas através de seu suporte para [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56b8b-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="56b8b-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="56b8b-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="56b8b-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="56b8b-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="56b8b-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="56b8b-269">BindingSource</span></span>|  
|<span data-ttu-id="56b8b-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="56b8b-270">DataGrid</span></span>|  
|<span data-ttu-id="56b8b-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="56b8b-271">DataGridView</span></span>|  
|<span data-ttu-id="56b8b-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="56b8b-272">DataNavigator</span></span>|  
|<span data-ttu-id="56b8b-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="56b8b-273">DomainUpDown</span></span>|  
|<span data-ttu-id="56b8b-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="56b8b-274">ErrorProvider</span></span>|  
|<span data-ttu-id="56b8b-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="56b8b-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="56b8b-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="56b8b-276">Form</span></span>|  
|<span data-ttu-id="56b8b-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="56b8b-277">LinkLabel</span></span>|  
|<span data-ttu-id="56b8b-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="56b8b-278">HelpProvider</span></span>|  
|<span data-ttu-id="56b8b-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="56b8b-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="56b8b-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="56b8b-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="56b8b-281">NumericUpDown</span></span>|  
|<span data-ttu-id="56b8b-282">Painel</span><span class="sxs-lookup"><span data-stu-id="56b8b-282">Panel</span></span>|  
|<span data-ttu-id="56b8b-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="56b8b-283">PictureBox</span></span>|  
|<span data-ttu-id="56b8b-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="56b8b-284">PrintDocument</span></span>|  
|<span data-ttu-id="56b8b-285">Controle PrintPreview</span><span class="sxs-lookup"><span data-stu-id="56b8b-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="56b8b-286">Caixa de diálogo PrintPreview</span><span class="sxs-lookup"><span data-stu-id="56b8b-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="56b8b-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="56b8b-287">PropertyGrid</span></span>|  
|<span data-ttu-id="56b8b-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="56b8b-288">UserControl</span></span>|  
|<span data-ttu-id="56b8b-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="56b8b-289">ToolStrip</span></span>|  
|<span data-ttu-id="56b8b-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="56b8b-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="56b8b-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="56b8b-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="56b8b-292">Separador</span><span class="sxs-lookup"><span data-stu-id="56b8b-292">Splitter</span></span>|  
|<span data-ttu-id="56b8b-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="56b8b-293">RaftingContainer</span></span>|  
|<span data-ttu-id="56b8b-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="56b8b-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56b8b-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56b8b-295">See Also</span></span>  
 <span data-ttu-id="56b8b-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="56b8b-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)</span></span>
