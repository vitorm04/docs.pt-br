---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: c59352f908c5f4a1fd2ca6dd631d26bb5d69f09a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441215"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="6825a-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="6825a-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="6825a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6825a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6825a-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="6825a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6825a-105">Este tópico contém informações sobre o suporte a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para controles padrão em aplicativos desenvolvidos para as estruturas [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6825a-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="6825a-106">Controles de Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="6825a-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="6825a-107">Todos os elementos de controle de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] que fornecem informações ou suporte para interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6825a-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6825a-108">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6825a-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="6825a-109">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="6825a-109">Win32 Controls</span></span>  
 <span data-ttu-id="6825a-110">A maioria dos controles de [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] são expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente em UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="6825a-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6825a-111">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6825a-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6825a-112">O suporte completo é fornecido somente para controles da versão 6 do ComCtrl32. dll (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="6825a-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="6825a-113">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="6825a-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6825a-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="6825a-114">Class name</span></span>|<span data-ttu-id="6825a-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="6825a-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6825a-116">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-116">Button</span></span>|<span data-ttu-id="6825a-117">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-117">Button</span></span>|  
|<span data-ttu-id="6825a-118">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-118">Button</span></span>|<span data-ttu-id="6825a-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6825a-119">RadioButton</span></span>|  
|<span data-ttu-id="6825a-120">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-120">Button</span></span>|<span data-ttu-id="6825a-121">Grupo</span><span class="sxs-lookup"><span data-stu-id="6825a-121">Group</span></span>|  
|<span data-ttu-id="6825a-122">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-122">Button</span></span>|<span data-ttu-id="6825a-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6825a-123">CheckBox</span></span>|  
|<span data-ttu-id="6825a-124">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-124">Button</span></span>|<span data-ttu-id="6825a-125">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="6825a-125">Hyperlink</span></span>|  
|<span data-ttu-id="6825a-126">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-126">Button</span></span>|<span data-ttu-id="6825a-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="6825a-127">SplitButton</span></span>|  
|<span data-ttu-id="6825a-128">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-128">Button</span></span>|<span data-ttu-id="6825a-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6825a-129">CheckBox</span></span>|  
|<span data-ttu-id="6825a-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="6825a-130">ComboBoxEx32</span></span>|<span data-ttu-id="6825a-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6825a-131">ComboBox</span></span>|  
|<span data-ttu-id="6825a-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6825a-132">ComboBox</span></span>|<span data-ttu-id="6825a-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6825a-133">ComboBox</span></span>|  
|<span data-ttu-id="6825a-134">Editar</span><span class="sxs-lookup"><span data-stu-id="6825a-134">Edit</span></span>|<span data-ttu-id="6825a-135">Documento</span><span class="sxs-lookup"><span data-stu-id="6825a-135">Document</span></span>|  
|<span data-ttu-id="6825a-136">Editar</span><span class="sxs-lookup"><span data-stu-id="6825a-136">Edit</span></span>|<span data-ttu-id="6825a-137">Editar</span><span class="sxs-lookup"><span data-stu-id="6825a-137">Edit</span></span>|  
|<span data-ttu-id="6825a-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="6825a-138">SysLink</span></span>|<span data-ttu-id="6825a-139">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="6825a-139">Hyperlink</span></span>|  
|<span data-ttu-id="6825a-140">Estático</span><span class="sxs-lookup"><span data-stu-id="6825a-140">Static</span></span>|<span data-ttu-id="6825a-141">Texto</span><span class="sxs-lookup"><span data-stu-id="6825a-141">Text</span></span>|  
|<span data-ttu-id="6825a-142">Estático</span><span class="sxs-lookup"><span data-stu-id="6825a-142">Static</span></span>|<span data-ttu-id="6825a-143">Imagem</span><span class="sxs-lookup"><span data-stu-id="6825a-143">Image</span></span>|  
|<span data-ttu-id="6825a-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="6825a-144">SysIPAddress32</span></span>|<span data-ttu-id="6825a-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6825a-145">Custom</span></span>|  
|<span data-ttu-id="6825a-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="6825a-146">SysHeader32</span></span>|<span data-ttu-id="6825a-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="6825a-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="6825a-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6825a-148">SysListView32</span></span>|<span data-ttu-id="6825a-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6825a-149">DataGrid</span></span>|  
|<span data-ttu-id="6825a-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6825a-150">SysListView32</span></span>|<span data-ttu-id="6825a-151">Lista</span><span class="sxs-lookup"><span data-stu-id="6825a-151">List</span></span>|  
|<span data-ttu-id="6825a-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="6825a-152">ListBox</span></span>|<span data-ttu-id="6825a-153">Lista</span><span class="sxs-lookup"><span data-stu-id="6825a-153">List</span></span>|  
|<span data-ttu-id="6825a-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="6825a-154">ListBox</span></span>|<span data-ttu-id="6825a-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="6825a-155">ListItem</span></span>|  
|<span data-ttu-id="6825a-156">#32768</span><span class="sxs-lookup"><span data-stu-id="6825a-156">#32768</span></span>|<span data-ttu-id="6825a-157">Menu</span><span class="sxs-lookup"><span data-stu-id="6825a-157">Menu</span></span>|  
|<span data-ttu-id="6825a-158">#32768</span><span class="sxs-lookup"><span data-stu-id="6825a-158">#32768</span></span>|<span data-ttu-id="6825a-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6825a-159">MenuItem</span></span>|  
|<span data-ttu-id="6825a-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="6825a-160">msctls_progress32</span></span>|<span data-ttu-id="6825a-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6825a-161">ProgressBar</span></span>|  
|<span data-ttu-id="6825a-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="6825a-162">RichEdit</span></span>|<span data-ttu-id="6825a-163">Documento.</span><span class="sxs-lookup"><span data-stu-id="6825a-163">Document.</span></span> <span data-ttu-id="6825a-164">Consulte a observação.</span><span class="sxs-lookup"><span data-stu-id="6825a-164">See note.</span></span>|  
|<span data-ttu-id="6825a-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="6825a-165">RichEdit20A</span></span>|<span data-ttu-id="6825a-166">Documento</span><span class="sxs-lookup"><span data-stu-id="6825a-166">Document</span></span>|  
|<span data-ttu-id="6825a-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="6825a-167">RichEdit20W</span></span>|<span data-ttu-id="6825a-168">Documento</span><span class="sxs-lookup"><span data-stu-id="6825a-168">Document</span></span>|  
|<span data-ttu-id="6825a-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="6825a-169">RichEdit50W</span></span>|<span data-ttu-id="6825a-170">Documento</span><span class="sxs-lookup"><span data-stu-id="6825a-170">Document</span></span>|  
|<span data-ttu-id="6825a-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="6825a-171">ScrollBar</span></span>|<span data-ttu-id="6825a-172">Controle Deslizante</span><span class="sxs-lookup"><span data-stu-id="6825a-172">Slider</span></span>|  
|<span data-ttu-id="6825a-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="6825a-173">msctls_trackbar32</span></span>|<span data-ttu-id="6825a-174">Controle Deslizante</span><span class="sxs-lookup"><span data-stu-id="6825a-174">Slider</span></span>|  
|<span data-ttu-id="6825a-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="6825a-175">msctls_updown32</span></span>|<span data-ttu-id="6825a-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="6825a-176">Spinner</span></span>|  
|<span data-ttu-id="6825a-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="6825a-177">msctls_statusbar32</span></span>|<span data-ttu-id="6825a-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6825a-178">StatusBar</span></span>|  
|<span data-ttu-id="6825a-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6825a-179">SysTabControl32</span></span>|<span data-ttu-id="6825a-180">Guia</span><span class="sxs-lookup"><span data-stu-id="6825a-180">Tab</span></span>|  
|<span data-ttu-id="6825a-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6825a-181">SysTabControl32</span></span>|<span data-ttu-id="6825a-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="6825a-182">TabItem</span></span>|  
|<span data-ttu-id="6825a-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-183">ToolbarWindow32</span></span>|<span data-ttu-id="6825a-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="6825a-184">ToolBar</span></span>|  
|<span data-ttu-id="6825a-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-185">ToolbarWindow32</span></span>|<span data-ttu-id="6825a-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6825a-186">MenuItem</span></span>|  
|<span data-ttu-id="6825a-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-187">ToolbarWindow32</span></span>|<span data-ttu-id="6825a-188">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-188">Button</span></span>|  
|<span data-ttu-id="6825a-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-189">ToolbarWindow32</span></span>|<span data-ttu-id="6825a-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6825a-190">CheckBox</span></span>|  
|<span data-ttu-id="6825a-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-191">ToolbarWindow32</span></span>|<span data-ttu-id="6825a-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6825a-192">RadioButton</span></span>|  
|<span data-ttu-id="6825a-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-193">ToolbarWindow32</span></span>|<span data-ttu-id="6825a-194">Separador</span><span class="sxs-lookup"><span data-stu-id="6825a-194">Separator</span></span>|  
|<span data-ttu-id="6825a-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="6825a-195">tooltips_class32</span></span>|<span data-ttu-id="6825a-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6825a-196">ToolTip</span></span>|  
|<span data-ttu-id="6825a-197">#32774</span><span class="sxs-lookup"><span data-stu-id="6825a-197">#32774</span></span>|<span data-ttu-id="6825a-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6825a-198">ToolTip</span></span>|  
|<span data-ttu-id="6825a-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="6825a-199">ReBarWindow32</span></span>|<span data-ttu-id="6825a-200">Barra de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="6825a-200">Toolbar</span></span>|  
|<span data-ttu-id="6825a-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6825a-201">SysTreeView32</span></span>|<span data-ttu-id="6825a-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="6825a-202">Tree</span></span>|  
|<span data-ttu-id="6825a-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6825a-203">SysTreeView32</span></span>|<span data-ttu-id="6825a-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="6825a-204">TreeItem</span></span>|  
  
 <span data-ttu-id="6825a-205">**Observação** O controle RichEdit tem suporte apenas para versões fornecidas com o Windows Vista (em RichEd20. dll versão 3,1 e posterior e MsftEdit. dll versão 4,1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="6825a-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="6825a-206">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="6825a-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="6825a-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="6825a-207">Class name</span></span>|<span data-ttu-id="6825a-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="6825a-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6825a-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="6825a-209">SysAnimate32</span></span>|<span data-ttu-id="6825a-210">Imagem</span><span class="sxs-lookup"><span data-stu-id="6825a-210">Image</span></span>|  
|<span data-ttu-id="6825a-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="6825a-211">SysPager</span></span>|<span data-ttu-id="6825a-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="6825a-212">Spinner</span></span>|  
|<span data-ttu-id="6825a-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="6825a-213">SysDateTimePick32</span></span>|<span data-ttu-id="6825a-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6825a-214">Custom</span></span>|  
|<span data-ttu-id="6825a-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="6825a-215">SysMonthCal32</span></span>|<span data-ttu-id="6825a-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="6825a-216">Calendar</span></span>|  
|<span data-ttu-id="6825a-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="6825a-217">MS_WINNOTE</span></span>|<span data-ttu-id="6825a-218">dessa</span><span class="sxs-lookup"><span data-stu-id="6825a-218">Tooltip</span></span>|  
|<span data-ttu-id="6825a-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="6825a-219">VBBubble</span></span>|<span data-ttu-id="6825a-220">dessa</span><span class="sxs-lookup"><span data-stu-id="6825a-220">Tooltip</span></span>|  
|<span data-ttu-id="6825a-221">ScrollBar (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="6825a-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="6825a-222">Controle Deslizante</span><span class="sxs-lookup"><span data-stu-id="6825a-222">Slider</span></span>|  
|<span data-ttu-id="6825a-223">Subgrade</span><span class="sxs-lookup"><span data-stu-id="6825a-223">SuperGrid</span></span>|<span data-ttu-id="6825a-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6825a-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="6825a-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6825a-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="6825a-226">Os controles de Windows Forms são expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente em UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="6825a-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6825a-227">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6825a-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6825a-228">Normalmente, Windows Forms controles que são wrappers gerenciados para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns têm suporte do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6825a-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6825a-229">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="6825a-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6825a-230">Nome da Classe</span><span class="sxs-lookup"><span data-stu-id="6825a-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="6825a-231">Botão</span><span class="sxs-lookup"><span data-stu-id="6825a-231">Button</span></span>|  
|<span data-ttu-id="6825a-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6825a-232">CheckBox</span></span>|  
|<span data-ttu-id="6825a-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="6825a-233">CheckedListBox</span></span>|  
|<span data-ttu-id="6825a-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="6825a-234">ColorDialog</span></span>|  
|<span data-ttu-id="6825a-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6825a-235">ComboBox</span></span>|  
|<span data-ttu-id="6825a-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="6825a-236">FolderBrowser</span></span>|  
|<span data-ttu-id="6825a-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="6825a-237">FontDialog</span></span>|  
|<span data-ttu-id="6825a-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="6825a-238">GroupBox</span></span>|  
|<span data-ttu-id="6825a-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="6825a-239">HscrollBar</span></span>|  
|<span data-ttu-id="6825a-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="6825a-240">ImageList</span></span>|  
|<span data-ttu-id="6825a-241">Rotular</span><span class="sxs-lookup"><span data-stu-id="6825a-241">Label</span></span>|  
|<span data-ttu-id="6825a-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="6825a-242">ListBox</span></span>|  
|<span data-ttu-id="6825a-243">ListView</span><span class="sxs-lookup"><span data-stu-id="6825a-243">ListView</span></span>|  
|<span data-ttu-id="6825a-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="6825a-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="6825a-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="6825a-245">MonthCalendar</span></span>|  
|<span data-ttu-id="6825a-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="6825a-246">NotifyIcon</span></span>|  
|<span data-ttu-id="6825a-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6825a-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="6825a-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="6825a-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="6825a-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6825a-249">PrintDialog</span></span>|  
|<span data-ttu-id="6825a-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6825a-250">ProgressBar</span></span>|  
|<span data-ttu-id="6825a-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6825a-251">RadioButton</span></span>|  
|<span data-ttu-id="6825a-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6825a-252">RichTextBox</span></span>|  
|<span data-ttu-id="6825a-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="6825a-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="6825a-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="6825a-254">ScrollableControl</span></span>|  
|<span data-ttu-id="6825a-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="6825a-255">SoundPlayer</span></span>|  
|<span data-ttu-id="6825a-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6825a-256">StatusBar</span></span>|  
|<span data-ttu-id="6825a-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="6825a-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="6825a-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="6825a-258">TextBox</span></span>|  
|<span data-ttu-id="6825a-259">{1&gt;Timer&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6825a-259">Timer</span></span>|  
|<span data-ttu-id="6825a-260">Barra de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="6825a-260">Toolbar</span></span>|  
|<span data-ttu-id="6825a-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6825a-261">ToolTip</span></span>|  
|<span data-ttu-id="6825a-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="6825a-262">TrackBar</span></span>|  
|<span data-ttu-id="6825a-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="6825a-263">TreeView</span></span>|  
|<span data-ttu-id="6825a-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="6825a-264">VscrollBar</span></span>|  
|<span data-ttu-id="6825a-265">Controlo</span><span class="sxs-lookup"><span data-stu-id="6825a-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="6825a-266">Os controles a seguir são expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] somente por meio de seu suporte para o Microsoft Acessibilidade Ativa.</span><span class="sxs-lookup"><span data-stu-id="6825a-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="6825a-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6825a-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="6825a-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="6825a-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="6825a-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="6825a-269">BindingSource</span></span>|  
|<span data-ttu-id="6825a-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6825a-270">DataGrid</span></span>|  
|<span data-ttu-id="6825a-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="6825a-271">DataGridView</span></span>|  
|<span data-ttu-id="6825a-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="6825a-272">DataNavigator</span></span>|  
|<span data-ttu-id="6825a-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="6825a-273">DomainUpDown</span></span>|  
|<span data-ttu-id="6825a-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="6825a-274">ErrorProvider</span></span>|  
|<span data-ttu-id="6825a-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6825a-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="6825a-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="6825a-276">Form</span></span>|  
|<span data-ttu-id="6825a-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6825a-277">LinkLabel</span></span>|  
|<span data-ttu-id="6825a-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="6825a-278">HelpProvider</span></span>|  
|<span data-ttu-id="6825a-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="6825a-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="6825a-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="6825a-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="6825a-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="6825a-281">NumericUpDown</span></span>|  
|<span data-ttu-id="6825a-282">Painel</span><span class="sxs-lookup"><span data-stu-id="6825a-282">Panel</span></span>|  
|<span data-ttu-id="6825a-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="6825a-283">PictureBox</span></span>|  
|<span data-ttu-id="6825a-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="6825a-284">PrintDocument</span></span>|  
|<span data-ttu-id="6825a-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="6825a-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="6825a-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="6825a-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="6825a-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="6825a-287">PropertyGrid</span></span>|  
|<span data-ttu-id="6825a-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="6825a-288">UserControl</span></span>|  
|<span data-ttu-id="6825a-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6825a-289">ToolStrip</span></span>|  
|<span data-ttu-id="6825a-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6825a-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="6825a-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="6825a-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="6825a-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="6825a-292">Splitter</span></span>|  
|<span data-ttu-id="6825a-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="6825a-293">RaftingContainer</span></span>|  
|<span data-ttu-id="6825a-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="6825a-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6825a-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6825a-295">See also</span></span>

- <span data-ttu-id="6825a-296">[UI Automation Control Types](ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)</span><span class="sxs-lookup"><span data-stu-id="6825a-296">[UI Automation Control Types](ui-automation-control-types.md)</span></span>
