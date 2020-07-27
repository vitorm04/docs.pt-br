---
title: Suporte de automação de interface do usuário para Controles Padrão
description: Obtenha informações sobre o suporte de automação da interface do usuário para controles padrão em aplicativos desenvolvidos para Windows Presentation Foundation (WPF), Win32 e Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166122"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="3b269-103">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="3b269-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="3b269-104">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3b269-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3b269-105">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="3b269-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3b269-106">Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o suporte para controles padrão em aplicativos desenvolvidos para as [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] estruturas do, Win32 e Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3b269-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="3b269-107">Controles de Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="3b269-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="3b269-108">Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte para interação do usuário têm suporte nativo completo para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3b269-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="3b269-109">Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3b269-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="3b269-110">Controles do Win32</span><span class="sxs-lookup"><span data-stu-id="3b269-110">Win32 Controls</span></span>  
 <span data-ttu-id="3b269-111">A maioria dos controles do Win32 é exposta a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] provedores do lado do cliente no UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="3b269-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="3b269-112">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3b269-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="3b269-113">O suporte completo é fornecido somente para controles da versão 6 do *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="3b269-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="3b269-114">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="3b269-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="3b269-115">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="3b269-115">Class name</span></span>|<span data-ttu-id="3b269-116">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="3b269-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="3b269-117">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-117">Button</span></span>|<span data-ttu-id="3b269-118">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-118">Button</span></span>|  
|<span data-ttu-id="3b269-119">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-119">Button</span></span>|<span data-ttu-id="3b269-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3b269-120">RadioButton</span></span>|  
|<span data-ttu-id="3b269-121">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-121">Button</span></span>|<span data-ttu-id="3b269-122">Agrupar</span><span class="sxs-lookup"><span data-stu-id="3b269-122">Group</span></span>|  
|<span data-ttu-id="3b269-123">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-123">Button</span></span>|<span data-ttu-id="3b269-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3b269-124">CheckBox</span></span>|  
|<span data-ttu-id="3b269-125">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-125">Button</span></span>|<span data-ttu-id="3b269-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="3b269-126">Hyperlink</span></span>|  
|<span data-ttu-id="3b269-127">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-127">Button</span></span>|<span data-ttu-id="3b269-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="3b269-128">SplitButton</span></span>|  
|<span data-ttu-id="3b269-129">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-129">Button</span></span>|<span data-ttu-id="3b269-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3b269-130">CheckBox</span></span>|  
|<span data-ttu-id="3b269-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="3b269-131">ComboBoxEx32</span></span>|<span data-ttu-id="3b269-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3b269-132">ComboBox</span></span>|  
|<span data-ttu-id="3b269-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3b269-133">ComboBox</span></span>|<span data-ttu-id="3b269-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3b269-134">ComboBox</span></span>|  
|<span data-ttu-id="3b269-135">Editar</span><span class="sxs-lookup"><span data-stu-id="3b269-135">Edit</span></span>|<span data-ttu-id="3b269-136">Document</span><span class="sxs-lookup"><span data-stu-id="3b269-136">Document</span></span>|  
|<span data-ttu-id="3b269-137">Editar</span><span class="sxs-lookup"><span data-stu-id="3b269-137">Edit</span></span>|<span data-ttu-id="3b269-138">Editar</span><span class="sxs-lookup"><span data-stu-id="3b269-138">Edit</span></span>|  
|<span data-ttu-id="3b269-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="3b269-139">SysLink</span></span>|<span data-ttu-id="3b269-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="3b269-140">Hyperlink</span></span>|  
|<span data-ttu-id="3b269-141">Estático</span><span class="sxs-lookup"><span data-stu-id="3b269-141">Static</span></span>|<span data-ttu-id="3b269-142">Texto</span><span class="sxs-lookup"><span data-stu-id="3b269-142">Text</span></span>|  
|<span data-ttu-id="3b269-143">Estático</span><span class="sxs-lookup"><span data-stu-id="3b269-143">Static</span></span>|<span data-ttu-id="3b269-144">Image</span><span class="sxs-lookup"><span data-stu-id="3b269-144">Image</span></span>|  
|<span data-ttu-id="3b269-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="3b269-145">SysIPAddress32</span></span>|<span data-ttu-id="3b269-146">Personalizado</span><span class="sxs-lookup"><span data-stu-id="3b269-146">Custom</span></span>|  
|<span data-ttu-id="3b269-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="3b269-147">SysHeader32</span></span>|<span data-ttu-id="3b269-148">Cabeçalho/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="3b269-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="3b269-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="3b269-149">SysListView32</span></span>|<span data-ttu-id="3b269-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3b269-150">DataGrid</span></span>|  
|<span data-ttu-id="3b269-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="3b269-151">SysListView32</span></span>|<span data-ttu-id="3b269-152">Lista</span><span class="sxs-lookup"><span data-stu-id="3b269-152">List</span></span>|  
|<span data-ttu-id="3b269-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="3b269-153">ListBox</span></span>|<span data-ttu-id="3b269-154">Lista</span><span class="sxs-lookup"><span data-stu-id="3b269-154">List</span></span>|  
|<span data-ttu-id="3b269-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="3b269-155">ListBox</span></span>|<span data-ttu-id="3b269-156">Item</span><span class="sxs-lookup"><span data-stu-id="3b269-156">ListItem</span></span>|  
|<span data-ttu-id="3b269-157">#32768</span><span class="sxs-lookup"><span data-stu-id="3b269-157">#32768</span></span>|<span data-ttu-id="3b269-158">Menu</span><span class="sxs-lookup"><span data-stu-id="3b269-158">Menu</span></span>|  
|<span data-ttu-id="3b269-159">#32768</span><span class="sxs-lookup"><span data-stu-id="3b269-159">#32768</span></span>|<span data-ttu-id="3b269-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3b269-160">MenuItem</span></span>|  
|<span data-ttu-id="3b269-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="3b269-161">msctls_progress32</span></span>|<span data-ttu-id="3b269-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3b269-162">ProgressBar</span></span>|  
|<span data-ttu-id="3b269-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="3b269-163">RichEdit</span></span>|<span data-ttu-id="3b269-164">Documento.</span><span class="sxs-lookup"><span data-stu-id="3b269-164">Document.</span></span> <span data-ttu-id="3b269-165">Veja a observação.</span><span class="sxs-lookup"><span data-stu-id="3b269-165">See note.</span></span>|  
|<span data-ttu-id="3b269-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="3b269-166">RichEdit20A</span></span>|<span data-ttu-id="3b269-167">Document</span><span class="sxs-lookup"><span data-stu-id="3b269-167">Document</span></span>|  
|<span data-ttu-id="3b269-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="3b269-168">RichEdit20W</span></span>|<span data-ttu-id="3b269-169">Document</span><span class="sxs-lookup"><span data-stu-id="3b269-169">Document</span></span>|  
|<span data-ttu-id="3b269-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="3b269-170">RichEdit50W</span></span>|<span data-ttu-id="3b269-171">Document</span><span class="sxs-lookup"><span data-stu-id="3b269-171">Document</span></span>|  
|<span data-ttu-id="3b269-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="3b269-172">ScrollBar</span></span>|<span data-ttu-id="3b269-173">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="3b269-173">Slider</span></span>|  
|<span data-ttu-id="3b269-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="3b269-174">msctls_trackbar32</span></span>|<span data-ttu-id="3b269-175">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="3b269-175">Slider</span></span>|  
|<span data-ttu-id="3b269-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="3b269-176">msctls_updown32</span></span>|<span data-ttu-id="3b269-177">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="3b269-177">Spinner</span></span>|  
|<span data-ttu-id="3b269-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="3b269-178">msctls_statusbar32</span></span>|<span data-ttu-id="3b269-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="3b269-179">StatusBar</span></span>|  
|<span data-ttu-id="3b269-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="3b269-180">SysTabControl32</span></span>|<span data-ttu-id="3b269-181">Tab</span><span class="sxs-lookup"><span data-stu-id="3b269-181">Tab</span></span>|  
|<span data-ttu-id="3b269-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="3b269-182">SysTabControl32</span></span>|<span data-ttu-id="3b269-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="3b269-183">TabItem</span></span>|  
|<span data-ttu-id="3b269-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-184">ToolbarWindow32</span></span>|<span data-ttu-id="3b269-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="3b269-185">ToolBar</span></span>|  
|<span data-ttu-id="3b269-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-186">ToolbarWindow32</span></span>|<span data-ttu-id="3b269-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3b269-187">MenuItem</span></span>|  
|<span data-ttu-id="3b269-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-188">ToolbarWindow32</span></span>|<span data-ttu-id="3b269-189">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-189">Button</span></span>|  
|<span data-ttu-id="3b269-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-190">ToolbarWindow32</span></span>|<span data-ttu-id="3b269-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3b269-191">CheckBox</span></span>|  
|<span data-ttu-id="3b269-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-192">ToolbarWindow32</span></span>|<span data-ttu-id="3b269-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3b269-193">RadioButton</span></span>|  
|<span data-ttu-id="3b269-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-194">ToolbarWindow32</span></span>|<span data-ttu-id="3b269-195">Separador</span><span class="sxs-lookup"><span data-stu-id="3b269-195">Separator</span></span>|  
|<span data-ttu-id="3b269-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="3b269-196">tooltips_class32</span></span>|<span data-ttu-id="3b269-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="3b269-197">ToolTip</span></span>|  
|<span data-ttu-id="3b269-198">#32774</span><span class="sxs-lookup"><span data-stu-id="3b269-198">#32774</span></span>|<span data-ttu-id="3b269-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="3b269-199">ToolTip</span></span>|  
|<span data-ttu-id="3b269-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="3b269-200">ReBarWindow32</span></span>|<span data-ttu-id="3b269-201">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="3b269-201">Toolbar</span></span>|  
|<span data-ttu-id="3b269-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="3b269-202">SysTreeView32</span></span>|<span data-ttu-id="3b269-203">Árvore</span><span class="sxs-lookup"><span data-stu-id="3b269-203">Tree</span></span>|  
|<span data-ttu-id="3b269-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="3b269-204">SysTreeView32</span></span>|<span data-ttu-id="3b269-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="3b269-205">TreeItem</span></span>|  
  
 <span data-ttu-id="3b269-206">**Observação** O controle RichEdit tem suporte apenas para versões fornecidas com o Windows Vista (no RichEd20.dll versão 3,1 e posterior e MsftEdit.dll versão 4,1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="3b269-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="3b269-207">Não há suporte para os seguintes controles.</span><span class="sxs-lookup"><span data-stu-id="3b269-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="3b269-208">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="3b269-208">Class name</span></span>|<span data-ttu-id="3b269-209">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="3b269-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="3b269-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="3b269-210">SysAnimate32</span></span>|<span data-ttu-id="3b269-211">Image</span><span class="sxs-lookup"><span data-stu-id="3b269-211">Image</span></span>|  
|<span data-ttu-id="3b269-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="3b269-212">SysPager</span></span>|<span data-ttu-id="3b269-213">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="3b269-213">Spinner</span></span>|  
|<span data-ttu-id="3b269-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="3b269-214">SysDateTimePick32</span></span>|<span data-ttu-id="3b269-215">Personalizado</span><span class="sxs-lookup"><span data-stu-id="3b269-215">Custom</span></span>|  
|<span data-ttu-id="3b269-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="3b269-216">SysMonthCal32</span></span>|<span data-ttu-id="3b269-217">Calendário</span><span class="sxs-lookup"><span data-stu-id="3b269-217">Calendar</span></span>|  
|<span data-ttu-id="3b269-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="3b269-218">MS_WINNOTE</span></span>|<span data-ttu-id="3b269-219">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="3b269-219">Tooltip</span></span>|  
|<span data-ttu-id="3b269-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="3b269-220">VBBubble</span></span>|<span data-ttu-id="3b269-221">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="3b269-221">Tooltip</span></span>|  
|<span data-ttu-id="3b269-222">ScrollBar (quando usado como um controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="3b269-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="3b269-223">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="3b269-223">Slider</span></span>|  
|<span data-ttu-id="3b269-224">Subgrade</span><span class="sxs-lookup"><span data-stu-id="3b269-224">SuperGrid</span></span>|<span data-ttu-id="3b269-225">Personalizado</span><span class="sxs-lookup"><span data-stu-id="3b269-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="3b269-226">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b269-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="3b269-227">Os controles de Windows Forms são expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente no UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="3b269-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="3b269-228">Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3b269-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="3b269-229">Normalmente, Windows Forms controles que são wrappers gerenciados para controles comuns do Win32 são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3b269-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="3b269-230">Há suporte para os controles a seguir.</span><span class="sxs-lookup"><span data-stu-id="3b269-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="3b269-231">Nome da Classe</span><span class="sxs-lookup"><span data-stu-id="3b269-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="3b269-232">Botão</span><span class="sxs-lookup"><span data-stu-id="3b269-232">Button</span></span>|  
|<span data-ttu-id="3b269-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3b269-233">CheckBox</span></span>|  
|<span data-ttu-id="3b269-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="3b269-234">CheckedListBox</span></span>|  
|<span data-ttu-id="3b269-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="3b269-235">ColorDialog</span></span>|  
|<span data-ttu-id="3b269-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3b269-236">ComboBox</span></span>|  
|<span data-ttu-id="3b269-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="3b269-237">FolderBrowser</span></span>|  
|<span data-ttu-id="3b269-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="3b269-238">FontDialog</span></span>|  
|<span data-ttu-id="3b269-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="3b269-239">GroupBox</span></span>|  
|<span data-ttu-id="3b269-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="3b269-240">HscrollBar</span></span>|  
|<span data-ttu-id="3b269-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="3b269-241">ImageList</span></span>|  
|<span data-ttu-id="3b269-242">Rotular</span><span class="sxs-lookup"><span data-stu-id="3b269-242">Label</span></span>|  
|<span data-ttu-id="3b269-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="3b269-243">ListBox</span></span>|  
|<span data-ttu-id="3b269-244">ListView</span><span class="sxs-lookup"><span data-stu-id="3b269-244">ListView</span></span>|  
|<span data-ttu-id="3b269-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3b269-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="3b269-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="3b269-246">MonthCalendar</span></span>|  
|<span data-ttu-id="3b269-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="3b269-247">NotifyIcon</span></span>|  
|<span data-ttu-id="3b269-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="3b269-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="3b269-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="3b269-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="3b269-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="3b269-250">PrintDialog</span></span>|  
|<span data-ttu-id="3b269-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3b269-251">ProgressBar</span></span>|  
|<span data-ttu-id="3b269-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3b269-252">RadioButton</span></span>|  
|<span data-ttu-id="3b269-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="3b269-253">RichTextBox</span></span>|  
|<span data-ttu-id="3b269-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="3b269-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="3b269-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="3b269-255">ScrollableControl</span></span>|  
|<span data-ttu-id="3b269-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="3b269-256">SoundPlayer</span></span>|  
|<span data-ttu-id="3b269-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="3b269-257">StatusBar</span></span>|  
|<span data-ttu-id="3b269-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="3b269-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="3b269-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="3b269-259">TextBox</span></span>|  
|<span data-ttu-id="3b269-260">Timer</span><span class="sxs-lookup"><span data-stu-id="3b269-260">Timer</span></span>|  
|<span data-ttu-id="3b269-261">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="3b269-261">Toolbar</span></span>|  
|<span data-ttu-id="3b269-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="3b269-262">ToolTip</span></span>|  
|<span data-ttu-id="3b269-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="3b269-263">TrackBar</span></span>|  
|<span data-ttu-id="3b269-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="3b269-264">TreeView</span></span>|  
|<span data-ttu-id="3b269-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="3b269-265">VscrollBar</span></span>|  
|<span data-ttu-id="3b269-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="3b269-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="3b269-267">Os controles a seguir são expostos [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas por meio de seu suporte para o Microsoft acessibilidade ativa.</span><span class="sxs-lookup"><span data-stu-id="3b269-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="3b269-268">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3b269-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="3b269-269">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="3b269-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="3b269-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="3b269-270">BindingSource</span></span>|  
|<span data-ttu-id="3b269-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3b269-271">DataGrid</span></span>|  
|<span data-ttu-id="3b269-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="3b269-272">DataGridView</span></span>|  
|<span data-ttu-id="3b269-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="3b269-273">DataNavigator</span></span>|  
|<span data-ttu-id="3b269-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="3b269-274">DomainUpDown</span></span>|  
|<span data-ttu-id="3b269-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="3b269-275">ErrorProvider</span></span>|  
|<span data-ttu-id="3b269-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3b269-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="3b269-277">Formulário</span><span class="sxs-lookup"><span data-stu-id="3b269-277">Form</span></span>|  
|<span data-ttu-id="3b269-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="3b269-278">LinkLabel</span></span>|  
|<span data-ttu-id="3b269-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="3b269-279">HelpProvider</span></span>|  
|<span data-ttu-id="3b269-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="3b269-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="3b269-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3b269-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="3b269-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="3b269-282">NumericUpDown</span></span>|  
|<span data-ttu-id="3b269-283">Painel</span><span class="sxs-lookup"><span data-stu-id="3b269-283">Panel</span></span>|  
|<span data-ttu-id="3b269-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="3b269-284">PictureBox</span></span>|  
|<span data-ttu-id="3b269-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="3b269-285">PrintDocument</span></span>|  
|<span data-ttu-id="3b269-286">Visualização-controle</span><span class="sxs-lookup"><span data-stu-id="3b269-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="3b269-287">Caixa de diálogo de visualização prévia</span><span class="sxs-lookup"><span data-stu-id="3b269-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="3b269-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="3b269-288">PropertyGrid</span></span>|  
|<span data-ttu-id="3b269-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="3b269-289">UserControl</span></span>|  
|<span data-ttu-id="3b269-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3b269-290">ToolStrip</span></span>|  
|<span data-ttu-id="3b269-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3b269-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="3b269-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="3b269-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="3b269-293">Splitter</span><span class="sxs-lookup"><span data-stu-id="3b269-293">Splitter</span></span>|  
|<span data-ttu-id="3b269-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="3b269-294">RaftingContainer</span></span>|  
|<span data-ttu-id="3b269-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="3b269-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b269-296">Confira também</span><span class="sxs-lookup"><span data-stu-id="3b269-296">See also</span></span>

- [<span data-ttu-id="3b269-297">Tipos de controle de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="3b269-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
