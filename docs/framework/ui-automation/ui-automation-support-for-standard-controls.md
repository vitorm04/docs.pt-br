---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 68fa7753be76b0681c40e540e86b11c89e7a8ca1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193873"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="6c69c-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="6c69c-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="6c69c-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6c69c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6c69c-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="6c69c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6c69c-105">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="6c69c-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="6c69c-106">Controles do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="6c69c-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="6c69c-107">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte à interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c69c-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6c69c-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c69c-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="6c69c-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="6c69c-109">Win32 Controls</span></span>  
 <span data-ttu-id="6c69c-110">A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="6c69c-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6c69c-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6c69c-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6c69c-112">Suporte completo é fornecido somente para controles de versão 6 do Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="6c69c-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="6c69c-113">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="6c69c-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6c69c-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="6c69c-114">Class name</span></span>|<span data-ttu-id="6c69c-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="6c69c-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6c69c-116">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-116">Button</span></span>|<span data-ttu-id="6c69c-117">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-117">Button</span></span>|  
|<span data-ttu-id="6c69c-118">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-118">Button</span></span>|<span data-ttu-id="6c69c-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6c69c-119">RadioButton</span></span>|  
|<span data-ttu-id="6c69c-120">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-120">Button</span></span>|<span data-ttu-id="6c69c-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="6c69c-121">Group</span></span>|  
|<span data-ttu-id="6c69c-122">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-122">Button</span></span>|<span data-ttu-id="6c69c-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-123">CheckBox</span></span>|  
|<span data-ttu-id="6c69c-124">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-124">Button</span></span>|<span data-ttu-id="6c69c-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="6c69c-125">Hyperlink</span></span>|  
|<span data-ttu-id="6c69c-126">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-126">Button</span></span>|<span data-ttu-id="6c69c-127">Botão de divisão</span><span class="sxs-lookup"><span data-stu-id="6c69c-127">SplitButton</span></span>|  
|<span data-ttu-id="6c69c-128">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-128">Button</span></span>|<span data-ttu-id="6c69c-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-129">CheckBox</span></span>|  
|<span data-ttu-id="6c69c-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="6c69c-130">ComboBoxEx32</span></span>|<span data-ttu-id="6c69c-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-131">ComboBox</span></span>|  
|<span data-ttu-id="6c69c-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-132">ComboBox</span></span>|<span data-ttu-id="6c69c-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-133">ComboBox</span></span>|  
|<span data-ttu-id="6c69c-134">Editar</span><span class="sxs-lookup"><span data-stu-id="6c69c-134">Edit</span></span>|<span data-ttu-id="6c69c-135">Documento</span><span class="sxs-lookup"><span data-stu-id="6c69c-135">Document</span></span>|  
|<span data-ttu-id="6c69c-136">Editar</span><span class="sxs-lookup"><span data-stu-id="6c69c-136">Edit</span></span>|<span data-ttu-id="6c69c-137">Editar</span><span class="sxs-lookup"><span data-stu-id="6c69c-137">Edit</span></span>|  
|<span data-ttu-id="6c69c-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="6c69c-138">SysLink</span></span>|<span data-ttu-id="6c69c-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="6c69c-139">Hyperlink</span></span>|  
|<span data-ttu-id="6c69c-140">Estático</span><span class="sxs-lookup"><span data-stu-id="6c69c-140">Static</span></span>|<span data-ttu-id="6c69c-141">Texto</span><span class="sxs-lookup"><span data-stu-id="6c69c-141">Text</span></span>|  
|<span data-ttu-id="6c69c-142">Estático</span><span class="sxs-lookup"><span data-stu-id="6c69c-142">Static</span></span>|<span data-ttu-id="6c69c-143">Image</span><span class="sxs-lookup"><span data-stu-id="6c69c-143">Image</span></span>|  
|<span data-ttu-id="6c69c-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="6c69c-144">SysIPAddress32</span></span>|<span data-ttu-id="6c69c-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6c69c-145">Custom</span></span>|  
|<span data-ttu-id="6c69c-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="6c69c-146">SysHeader32</span></span>|<span data-ttu-id="6c69c-147">Cabeçalho/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="6c69c-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="6c69c-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6c69c-148">SysListView32</span></span>|<span data-ttu-id="6c69c-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6c69c-149">DataGrid</span></span>|  
|<span data-ttu-id="6c69c-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6c69c-150">SysListView32</span></span>|<span data-ttu-id="6c69c-151">Lista</span><span class="sxs-lookup"><span data-stu-id="6c69c-151">List</span></span>|  
|<span data-ttu-id="6c69c-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-152">ListBox</span></span>|<span data-ttu-id="6c69c-153">Lista</span><span class="sxs-lookup"><span data-stu-id="6c69c-153">List</span></span>|  
|<span data-ttu-id="6c69c-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-154">ListBox</span></span>|<span data-ttu-id="6c69c-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="6c69c-155">ListItem</span></span>|  
|<span data-ttu-id="6c69c-156">#32768</span><span class="sxs-lookup"><span data-stu-id="6c69c-156">#32768</span></span>|<span data-ttu-id="6c69c-157">Menu</span><span class="sxs-lookup"><span data-stu-id="6c69c-157">Menu</span></span>|  
|<span data-ttu-id="6c69c-158">#32768</span><span class="sxs-lookup"><span data-stu-id="6c69c-158">#32768</span></span>|<span data-ttu-id="6c69c-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6c69c-159">MenuItem</span></span>|  
|<span data-ttu-id="6c69c-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="6c69c-160">msctls_progress32</span></span>|<span data-ttu-id="6c69c-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-161">ProgressBar</span></span>|  
|<span data-ttu-id="6c69c-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="6c69c-162">RichEdit</span></span>|<span data-ttu-id="6c69c-163">Documento.</span><span class="sxs-lookup"><span data-stu-id="6c69c-163">Document.</span></span> <span data-ttu-id="6c69c-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="6c69c-164">See note.</span></span>|  
|<span data-ttu-id="6c69c-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="6c69c-165">RichEdit20A</span></span>|<span data-ttu-id="6c69c-166">Documento</span><span class="sxs-lookup"><span data-stu-id="6c69c-166">Document</span></span>|  
|<span data-ttu-id="6c69c-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="6c69c-167">RichEdit20W</span></span>|<span data-ttu-id="6c69c-168">Documento</span><span class="sxs-lookup"><span data-stu-id="6c69c-168">Document</span></span>|  
|<span data-ttu-id="6c69c-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="6c69c-169">RichEdit50W</span></span>|<span data-ttu-id="6c69c-170">Documento</span><span class="sxs-lookup"><span data-stu-id="6c69c-170">Document</span></span>|  
|<span data-ttu-id="6c69c-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-171">ScrollBar</span></span>|<span data-ttu-id="6c69c-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="6c69c-172">Slider</span></span>|  
|<span data-ttu-id="6c69c-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="6c69c-173">msctls_trackbar32</span></span>|<span data-ttu-id="6c69c-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="6c69c-174">Slider</span></span>|  
|<span data-ttu-id="6c69c-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="6c69c-175">msctls_updown32</span></span>|<span data-ttu-id="6c69c-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="6c69c-176">Spinner</span></span>|  
|<span data-ttu-id="6c69c-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="6c69c-177">msctls_statusbar32</span></span>|<span data-ttu-id="6c69c-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-178">StatusBar</span></span>|  
|<span data-ttu-id="6c69c-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6c69c-179">SysTabControl32</span></span>|<span data-ttu-id="6c69c-180">Tabulação</span><span class="sxs-lookup"><span data-stu-id="6c69c-180">Tab</span></span>|  
|<span data-ttu-id="6c69c-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6c69c-181">SysTabControl32</span></span>|<span data-ttu-id="6c69c-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="6c69c-182">TabItem</span></span>|  
|<span data-ttu-id="6c69c-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-183">ToolbarWindow32</span></span>|<span data-ttu-id="6c69c-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-184">ToolBar</span></span>|  
|<span data-ttu-id="6c69c-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-185">ToolbarWindow32</span></span>|<span data-ttu-id="6c69c-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6c69c-186">MenuItem</span></span>|  
|<span data-ttu-id="6c69c-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-187">ToolbarWindow32</span></span>|<span data-ttu-id="6c69c-188">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-188">Button</span></span>|  
|<span data-ttu-id="6c69c-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-189">ToolbarWindow32</span></span>|<span data-ttu-id="6c69c-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-190">CheckBox</span></span>|  
|<span data-ttu-id="6c69c-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-191">ToolbarWindow32</span></span>|<span data-ttu-id="6c69c-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6c69c-192">RadioButton</span></span>|  
|<span data-ttu-id="6c69c-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-193">ToolbarWindow32</span></span>|<span data-ttu-id="6c69c-194">Separador</span><span class="sxs-lookup"><span data-stu-id="6c69c-194">Separator</span></span>|  
|<span data-ttu-id="6c69c-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="6c69c-195">tooltips_class32</span></span>|<span data-ttu-id="6c69c-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6c69c-196">ToolTip</span></span>|  
|<span data-ttu-id="6c69c-197">#32774</span><span class="sxs-lookup"><span data-stu-id="6c69c-197">#32774</span></span>|<span data-ttu-id="6c69c-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6c69c-198">ToolTip</span></span>|  
|<span data-ttu-id="6c69c-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="6c69c-199">ReBarWindow32</span></span>|<span data-ttu-id="6c69c-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="6c69c-200">Toolbar</span></span>|  
|<span data-ttu-id="6c69c-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6c69c-201">SysTreeView32</span></span>|<span data-ttu-id="6c69c-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="6c69c-202">Tree</span></span>|  
|<span data-ttu-id="6c69c-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6c69c-203">SysTreeView32</span></span>|<span data-ttu-id="6c69c-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="6c69c-204">TreeItem</span></span>|  
  
 <span data-ttu-id="6c69c-205">**Observação** RichEdit o controle tem suporte somente para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (em RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posteriores).</span><span class="sxs-lookup"><span data-stu-id="6c69c-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="6c69c-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="6c69c-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="6c69c-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="6c69c-207">Class name</span></span>|<span data-ttu-id="6c69c-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="6c69c-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6c69c-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="6c69c-209">SysAnimate32</span></span>|<span data-ttu-id="6c69c-210">Image</span><span class="sxs-lookup"><span data-stu-id="6c69c-210">Image</span></span>|  
|<span data-ttu-id="6c69c-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="6c69c-211">SysPager</span></span>|<span data-ttu-id="6c69c-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="6c69c-212">Spinner</span></span>|  
|<span data-ttu-id="6c69c-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="6c69c-213">SysDateTimePick32</span></span>|<span data-ttu-id="6c69c-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6c69c-214">Custom</span></span>|  
|<span data-ttu-id="6c69c-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="6c69c-215">SysMonthCal32</span></span>|<span data-ttu-id="6c69c-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="6c69c-216">Calendar</span></span>|  
|<span data-ttu-id="6c69c-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="6c69c-217">MS_WINNOTE</span></span>|<span data-ttu-id="6c69c-218">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="6c69c-218">Tooltip</span></span>|  
|<span data-ttu-id="6c69c-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="6c69c-219">VBBubble</span></span>|<span data-ttu-id="6c69c-220">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="6c69c-220">Tooltip</span></span>|  
|<span data-ttu-id="6c69c-221">Barra de rolagem (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="6c69c-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="6c69c-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="6c69c-222">Slider</span></span>|  
|<span data-ttu-id="6c69c-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="6c69c-223">SuperGrid</span></span>|<span data-ttu-id="6c69c-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6c69c-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="6c69c-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c69c-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="6c69c-226">Controles dos Windows Forms são expostos ao [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders.</span><span class="sxs-lookup"><span data-stu-id="6c69c-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6c69c-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6c69c-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6c69c-228">Normalmente, controles de formulários do Windows que são gerenciados wrappers [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c69c-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6c69c-229">Os seguintes controles têm suporte.</span><span class="sxs-lookup"><span data-stu-id="6c69c-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6c69c-230">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="6c69c-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="6c69c-231">Botão</span><span class="sxs-lookup"><span data-stu-id="6c69c-231">Button</span></span>|  
|<span data-ttu-id="6c69c-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-232">CheckBox</span></span>|  
|<span data-ttu-id="6c69c-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-233">CheckedListBox</span></span>|  
|<span data-ttu-id="6c69c-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="6c69c-234">ColorDialog</span></span>|  
|<span data-ttu-id="6c69c-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-235">ComboBox</span></span>|  
|<span data-ttu-id="6c69c-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="6c69c-236">FolderBrowser</span></span>|  
|<span data-ttu-id="6c69c-237">FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="6c69c-237">FontDialog</span></span>|  
|<span data-ttu-id="6c69c-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-238">GroupBox</span></span>|  
|<span data-ttu-id="6c69c-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-239">HscrollBar</span></span>|  
|<span data-ttu-id="6c69c-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="6c69c-240">ImageList</span></span>|  
|<span data-ttu-id="6c69c-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="6c69c-241">Label</span></span>|  
|<span data-ttu-id="6c69c-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-242">ListBox</span></span>|  
|<span data-ttu-id="6c69c-243">ListView</span><span class="sxs-lookup"><span data-stu-id="6c69c-243">ListView</span></span>|  
|<span data-ttu-id="6c69c-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="6c69c-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="6c69c-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="6c69c-245">MonthCalendar</span></span>|  
|<span data-ttu-id="6c69c-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="6c69c-246">NotifyIcon</span></span>|  
|<span data-ttu-id="6c69c-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6c69c-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="6c69c-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="6c69c-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="6c69c-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6c69c-249">PrintDialog</span></span>|  
|<span data-ttu-id="6c69c-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-250">ProgressBar</span></span>|  
|<span data-ttu-id="6c69c-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6c69c-251">RadioButton</span></span>|  
|<span data-ttu-id="6c69c-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-252">RichTextBox</span></span>|  
|<span data-ttu-id="6c69c-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="6c69c-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="6c69c-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="6c69c-254">ScrollableControl</span></span>|  
|<span data-ttu-id="6c69c-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="6c69c-255">SoundPlayer</span></span>|  
|<span data-ttu-id="6c69c-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-256">StatusBar</span></span>|  
|<span data-ttu-id="6c69c-257">TabPage/TabControl</span><span class="sxs-lookup"><span data-stu-id="6c69c-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="6c69c-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-258">TextBox</span></span>|  
|<span data-ttu-id="6c69c-259">Temporizador</span><span class="sxs-lookup"><span data-stu-id="6c69c-259">Timer</span></span>|  
|<span data-ttu-id="6c69c-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="6c69c-260">Toolbar</span></span>|  
|<span data-ttu-id="6c69c-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6c69c-261">ToolTip</span></span>|  
|<span data-ttu-id="6c69c-262">Barra de controle</span><span class="sxs-lookup"><span data-stu-id="6c69c-262">TrackBar</span></span>|  
|<span data-ttu-id="6c69c-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="6c69c-263">TreeView</span></span>|  
|<span data-ttu-id="6c69c-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="6c69c-264">VscrollBar</span></span>|  
|<span data-ttu-id="6c69c-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="6c69c-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="6c69c-266">Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] somente através de seu suporte [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c69c-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="6c69c-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6c69c-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="6c69c-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="6c69c-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="6c69c-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="6c69c-269">BindingSource</span></span>|  
|<span data-ttu-id="6c69c-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6c69c-270">DataGrid</span></span>|  
|<span data-ttu-id="6c69c-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="6c69c-271">DataGridView</span></span>|  
|<span data-ttu-id="6c69c-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="6c69c-272">DataNavigator</span></span>|  
|<span data-ttu-id="6c69c-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="6c69c-273">DomainUpDown</span></span>|  
|<span data-ttu-id="6c69c-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="6c69c-274">ErrorProvider</span></span>|  
|<span data-ttu-id="6c69c-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6c69c-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="6c69c-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="6c69c-276">Form</span></span>|  
|<span data-ttu-id="6c69c-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6c69c-277">LinkLabel</span></span>|  
|<span data-ttu-id="6c69c-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="6c69c-278">HelpProvider</span></span>|  
|<span data-ttu-id="6c69c-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="6c69c-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="6c69c-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="6c69c-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="6c69c-281">NumericUpDown</span></span>|  
|<span data-ttu-id="6c69c-282">Painel</span><span class="sxs-lookup"><span data-stu-id="6c69c-282">Panel</span></span>|  
|<span data-ttu-id="6c69c-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="6c69c-283">PictureBox</span></span>|  
|<span data-ttu-id="6c69c-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="6c69c-284">PrintDocument</span></span>|  
|<span data-ttu-id="6c69c-285">Controle PrintPreview</span><span class="sxs-lookup"><span data-stu-id="6c69c-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="6c69c-286">Caixa de diálogo PrintPreview</span><span class="sxs-lookup"><span data-stu-id="6c69c-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="6c69c-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="6c69c-287">PropertyGrid</span></span>|  
|<span data-ttu-id="6c69c-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="6c69c-288">UserControl</span></span>|  
|<span data-ttu-id="6c69c-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6c69c-289">ToolStrip</span></span>|  
|<span data-ttu-id="6c69c-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6c69c-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="6c69c-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="6c69c-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="6c69c-292">Divisor</span><span class="sxs-lookup"><span data-stu-id="6c69c-292">Splitter</span></span>|  
|<span data-ttu-id="6c69c-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="6c69c-293">RaftingContainer</span></span>|  
|<span data-ttu-id="6c69c-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="6c69c-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c69c-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c69c-295">See Also</span></span>  
 <span data-ttu-id="6c69c-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="6c69c-296">[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)</span></span>
