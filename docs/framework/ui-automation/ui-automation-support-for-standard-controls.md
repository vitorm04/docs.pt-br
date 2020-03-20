---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179860"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="8c6ee-102">Suporte de automação de interface do usuário para Controles Padrão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="8c6ee-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8c6ee-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="8c6ee-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8c6ee-105">Este tópico contém [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informações sobre o suporte a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]controles padrão em aplicativos desenvolvidos para as estruturas, Win32 e Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="8c6ee-106">Controles da Fundação de Apresentação do Windows</span><span class="sxs-lookup"><span data-stu-id="8c6ee-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="8c6ee-107">Todos [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] os elementos de controle que fornecem informações [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ou suporte para interação do usuário têm suporte nativo completo para .</span><span class="sxs-lookup"><span data-stu-id="8c6ee-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="8c6ee-108">Outros elementos, como painéis, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]não são visíveis para .</span><span class="sxs-lookup"><span data-stu-id="8c6ee-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="8c6ee-109">Controles Win32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-109">Win32 Controls</span></span>  
 <span data-ttu-id="8c6ee-110">A maioria dos controles Win32 são expostos através [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] de provedores do lado do cliente em UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="8c6ee-111">Este conjunto é automaticamente registrado para uso com aplicativos clientes de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="8c6ee-112">O suporte completo é fornecido apenas para controles da versão 6 do *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="8c6ee-113">Os seguintes controles são suportados.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="8c6ee-114">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="8c6ee-114">Class name</span></span>|<span data-ttu-id="8c6ee-115">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="8c6ee-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="8c6ee-116">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-116">Button</span></span>|<span data-ttu-id="8c6ee-117">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-117">Button</span></span>|  
|<span data-ttu-id="8c6ee-118">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-118">Button</span></span>|<span data-ttu-id="8c6ee-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="8c6ee-119">RadioButton</span></span>|  
|<span data-ttu-id="8c6ee-120">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-120">Button</span></span>|<span data-ttu-id="8c6ee-121">Agrupar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-121">Group</span></span>|  
|<span data-ttu-id="8c6ee-122">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-122">Button</span></span>|<span data-ttu-id="8c6ee-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-123">CheckBox</span></span>|  
|<span data-ttu-id="8c6ee-124">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-124">Button</span></span>|<span data-ttu-id="8c6ee-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="8c6ee-125">Hyperlink</span></span>|  
|<span data-ttu-id="8c6ee-126">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-126">Button</span></span>|<span data-ttu-id="8c6ee-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="8c6ee-127">SplitButton</span></span>|  
|<span data-ttu-id="8c6ee-128">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-128">Button</span></span>|<span data-ttu-id="8c6ee-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-129">CheckBox</span></span>|  
|<span data-ttu-id="8c6ee-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-130">ComboBoxEx32</span></span>|<span data-ttu-id="8c6ee-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-131">ComboBox</span></span>|  
|<span data-ttu-id="8c6ee-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-132">ComboBox</span></span>|<span data-ttu-id="8c6ee-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-133">ComboBox</span></span>|  
|<span data-ttu-id="8c6ee-134">Editar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-134">Edit</span></span>|<span data-ttu-id="8c6ee-135">Document</span><span class="sxs-lookup"><span data-stu-id="8c6ee-135">Document</span></span>|  
|<span data-ttu-id="8c6ee-136">Editar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-136">Edit</span></span>|<span data-ttu-id="8c6ee-137">Editar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-137">Edit</span></span>|  
|<span data-ttu-id="8c6ee-138">Syslink</span><span class="sxs-lookup"><span data-stu-id="8c6ee-138">SysLink</span></span>|<span data-ttu-id="8c6ee-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="8c6ee-139">Hyperlink</span></span>|  
|<span data-ttu-id="8c6ee-140">Estático</span><span class="sxs-lookup"><span data-stu-id="8c6ee-140">Static</span></span>|<span data-ttu-id="8c6ee-141">Texto</span><span class="sxs-lookup"><span data-stu-id="8c6ee-141">Text</span></span>|  
|<span data-ttu-id="8c6ee-142">Estático</span><span class="sxs-lookup"><span data-stu-id="8c6ee-142">Static</span></span>|<span data-ttu-id="8c6ee-143">Imagem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-143">Image</span></span>|  
|<span data-ttu-id="8c6ee-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-144">SysIPAddress32</span></span>|<span data-ttu-id="8c6ee-145">Personalizado</span><span class="sxs-lookup"><span data-stu-id="8c6ee-145">Custom</span></span>|  
|<span data-ttu-id="8c6ee-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-146">SysHeader32</span></span>|<span data-ttu-id="8c6ee-147">Cabeçalho/cabeçalhoItem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="8c6ee-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-148">SysListView32</span></span>|<span data-ttu-id="8c6ee-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="8c6ee-149">DataGrid</span></span>|  
|<span data-ttu-id="8c6ee-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-150">SysListView32</span></span>|<span data-ttu-id="8c6ee-151">Lista</span><span class="sxs-lookup"><span data-stu-id="8c6ee-151">List</span></span>|  
|<span data-ttu-id="8c6ee-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-152">ListBox</span></span>|<span data-ttu-id="8c6ee-153">Lista</span><span class="sxs-lookup"><span data-stu-id="8c6ee-153">List</span></span>|  
|<span data-ttu-id="8c6ee-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-154">ListBox</span></span>|<span data-ttu-id="8c6ee-155">Listitem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-155">ListItem</span></span>|  
|<span data-ttu-id="8c6ee-156">#32768</span><span class="sxs-lookup"><span data-stu-id="8c6ee-156">#32768</span></span>|<span data-ttu-id="8c6ee-157">Menu</span><span class="sxs-lookup"><span data-stu-id="8c6ee-157">Menu</span></span>|  
|<span data-ttu-id="8c6ee-158">#32768</span><span class="sxs-lookup"><span data-stu-id="8c6ee-158">#32768</span></span>|<span data-ttu-id="8c6ee-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-159">MenuItem</span></span>|  
|<span data-ttu-id="8c6ee-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-160">msctls_progress32</span></span>|<span data-ttu-id="8c6ee-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-161">ProgressBar</span></span>|  
|<span data-ttu-id="8c6ee-162">Richedit</span><span class="sxs-lookup"><span data-stu-id="8c6ee-162">RichEdit</span></span>|<span data-ttu-id="8c6ee-163">Documento.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-163">Document.</span></span> <span data-ttu-id="8c6ee-164">Veja a nota.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-164">See note.</span></span>|  
|<span data-ttu-id="8c6ee-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="8c6ee-165">RichEdit20A</span></span>|<span data-ttu-id="8c6ee-166">Document</span><span class="sxs-lookup"><span data-stu-id="8c6ee-166">Document</span></span>|  
|<span data-ttu-id="8c6ee-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="8c6ee-167">RichEdit20W</span></span>|<span data-ttu-id="8c6ee-168">Document</span><span class="sxs-lookup"><span data-stu-id="8c6ee-168">Document</span></span>|  
|<span data-ttu-id="8c6ee-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="8c6ee-169">RichEdit50W</span></span>|<span data-ttu-id="8c6ee-170">Document</span><span class="sxs-lookup"><span data-stu-id="8c6ee-170">Document</span></span>|  
|<span data-ttu-id="8c6ee-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-171">ScrollBar</span></span>|<span data-ttu-id="8c6ee-172">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="8c6ee-172">Slider</span></span>|  
|<span data-ttu-id="8c6ee-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-173">msctls_trackbar32</span></span>|<span data-ttu-id="8c6ee-174">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="8c6ee-174">Slider</span></span>|  
|<span data-ttu-id="8c6ee-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-175">msctls_updown32</span></span>|<span data-ttu-id="8c6ee-176">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="8c6ee-176">Spinner</span></span>|  
|<span data-ttu-id="8c6ee-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-177">msctls_statusbar32</span></span>|<span data-ttu-id="8c6ee-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-178">StatusBar</span></span>|  
|<span data-ttu-id="8c6ee-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-179">SysTabControl32</span></span>|<span data-ttu-id="8c6ee-180">Tab</span><span class="sxs-lookup"><span data-stu-id="8c6ee-180">Tab</span></span>|  
|<span data-ttu-id="8c6ee-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-181">SysTabControl32</span></span>|<span data-ttu-id="8c6ee-182">Tabitem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-182">TabItem</span></span>|  
|<span data-ttu-id="8c6ee-183">Barra de ferramentasJanela32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-183">ToolbarWindow32</span></span>|<span data-ttu-id="8c6ee-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-184">ToolBar</span></span>|  
|<span data-ttu-id="8c6ee-185">Barra de ferramentasJanela32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-185">ToolbarWindow32</span></span>|<span data-ttu-id="8c6ee-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-186">MenuItem</span></span>|  
|<span data-ttu-id="8c6ee-187">Barra de ferramentasJanela32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-187">ToolbarWindow32</span></span>|<span data-ttu-id="8c6ee-188">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-188">Button</span></span>|  
|<span data-ttu-id="8c6ee-189">Barra de ferramentasJanela32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-189">ToolbarWindow32</span></span>|<span data-ttu-id="8c6ee-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-190">CheckBox</span></span>|  
|<span data-ttu-id="8c6ee-191">Barra de ferramentasJanela32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-191">ToolbarWindow32</span></span>|<span data-ttu-id="8c6ee-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="8c6ee-192">RadioButton</span></span>|  
|<span data-ttu-id="8c6ee-193">Barra de ferramentasJanela32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-193">ToolbarWindow32</span></span>|<span data-ttu-id="8c6ee-194">Separador</span><span class="sxs-lookup"><span data-stu-id="8c6ee-194">Separator</span></span>|  
|<span data-ttu-id="8c6ee-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-195">tooltips_class32</span></span>|<span data-ttu-id="8c6ee-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="8c6ee-196">ToolTip</span></span>|  
|<span data-ttu-id="8c6ee-197">#32774</span><span class="sxs-lookup"><span data-stu-id="8c6ee-197">#32774</span></span>|<span data-ttu-id="8c6ee-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="8c6ee-198">ToolTip</span></span>|  
|<span data-ttu-id="8c6ee-199">RebarWindow32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-199">ReBarWindow32</span></span>|<span data-ttu-id="8c6ee-200">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="8c6ee-200">Toolbar</span></span>|  
|<span data-ttu-id="8c6ee-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-201">SysTreeView32</span></span>|<span data-ttu-id="8c6ee-202">Árvore</span><span class="sxs-lookup"><span data-stu-id="8c6ee-202">Tree</span></span>|  
|<span data-ttu-id="8c6ee-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-203">SysTreeView32</span></span>|<span data-ttu-id="8c6ee-204">Treeitem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-204">TreeItem</span></span>|  
  
 <span data-ttu-id="8c6ee-205">**Nota** O controle RichEdit é suportado apenas para versões enviadas com o Windows Vista (na versão RichEd20.dll 3.1 e posteriores, e na versão 4.1 do MsftEdit.dll e posteriores).</span><span class="sxs-lookup"><span data-stu-id="8c6ee-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="8c6ee-206">Os seguintes controles não são suportados.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="8c6ee-207">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="8c6ee-207">Class name</span></span>|<span data-ttu-id="8c6ee-208">Tipo de controle</span><span class="sxs-lookup"><span data-stu-id="8c6ee-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="8c6ee-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-209">SysAnimate32</span></span>|<span data-ttu-id="8c6ee-210">Imagem</span><span class="sxs-lookup"><span data-stu-id="8c6ee-210">Image</span></span>|  
|<span data-ttu-id="8c6ee-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="8c6ee-211">SysPager</span></span>|<span data-ttu-id="8c6ee-212">Controle giratório</span><span class="sxs-lookup"><span data-stu-id="8c6ee-212">Spinner</span></span>|  
|<span data-ttu-id="8c6ee-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-213">SysDateTimePick32</span></span>|<span data-ttu-id="8c6ee-214">Personalizado</span><span class="sxs-lookup"><span data-stu-id="8c6ee-214">Custom</span></span>|  
|<span data-ttu-id="8c6ee-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="8c6ee-215">SysMonthCal32</span></span>|<span data-ttu-id="8c6ee-216">Calendário</span><span class="sxs-lookup"><span data-stu-id="8c6ee-216">Calendar</span></span>|  
|<span data-ttu-id="8c6ee-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="8c6ee-217">MS_WINNOTE</span></span>|<span data-ttu-id="8c6ee-218">Dica de Ferramenta</span><span class="sxs-lookup"><span data-stu-id="8c6ee-218">Tooltip</span></span>|  
|<span data-ttu-id="8c6ee-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="8c6ee-219">VBBubble</span></span>|<span data-ttu-id="8c6ee-220">Dica de Ferramenta</span><span class="sxs-lookup"><span data-stu-id="8c6ee-220">Tooltip</span></span>|  
|<span data-ttu-id="8c6ee-221">ScrollBar (quando usado como controle autônomo)</span><span class="sxs-lookup"><span data-stu-id="8c6ee-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="8c6ee-222">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="8c6ee-222">Slider</span></span>|  
|<span data-ttu-id="8c6ee-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="8c6ee-223">SuperGrid</span></span>|<span data-ttu-id="8c6ee-224">Personalizado</span><span class="sxs-lookup"><span data-stu-id="8c6ee-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="8c6ee-225">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c6ee-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="8c6ee-226">Os controles do Windows [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Forms são expostos através de provedores do lado do cliente em UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="8c6ee-227">Este conjunto é automaticamente registrado para uso com aplicativos clientes de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="8c6ee-228">Normalmente, os controles do Windows Forms que são invólucros gerenciados para controles comuns do Win32 são suportados por [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c6ee-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="8c6ee-229">Os seguintes controles são suportados.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="8c6ee-230">Nome da Classe</span><span class="sxs-lookup"><span data-stu-id="8c6ee-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="8c6ee-231">Botão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-231">Button</span></span>|  
|<span data-ttu-id="8c6ee-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-232">CheckBox</span></span>|  
|<span data-ttu-id="8c6ee-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-233">CheckedListBox</span></span>|  
|<span data-ttu-id="8c6ee-234">Colordialog</span><span class="sxs-lookup"><span data-stu-id="8c6ee-234">ColorDialog</span></span>|  
|<span data-ttu-id="8c6ee-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-235">ComboBox</span></span>|  
|<span data-ttu-id="8c6ee-236">Folderbrowser</span><span class="sxs-lookup"><span data-stu-id="8c6ee-236">FolderBrowser</span></span>|  
|<span data-ttu-id="8c6ee-237">Fontdialog</span><span class="sxs-lookup"><span data-stu-id="8c6ee-237">FontDialog</span></span>|  
|<span data-ttu-id="8c6ee-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-238">GroupBox</span></span>|  
|<span data-ttu-id="8c6ee-239">Hscrollbar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-239">HscrollBar</span></span>|  
|<span data-ttu-id="8c6ee-240">Imagelist</span><span class="sxs-lookup"><span data-stu-id="8c6ee-240">ImageList</span></span>|  
|<span data-ttu-id="8c6ee-241">Rótulo</span><span class="sxs-lookup"><span data-stu-id="8c6ee-241">Label</span></span>|  
|<span data-ttu-id="8c6ee-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-242">ListBox</span></span>|  
|<span data-ttu-id="8c6ee-243">ListView</span><span class="sxs-lookup"><span data-stu-id="8c6ee-243">ListView</span></span>|  
|<span data-ttu-id="8c6ee-244">Menu principal/menu de contexto</span><span class="sxs-lookup"><span data-stu-id="8c6ee-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="8c6ee-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-245">MonthCalendar</span></span>|  
|<span data-ttu-id="8c6ee-246">Notifyicon</span><span class="sxs-lookup"><span data-stu-id="8c6ee-246">NotifyIcon</span></span>|  
|<span data-ttu-id="8c6ee-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8c6ee-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="8c6ee-248">Pagesetupdialog</span><span class="sxs-lookup"><span data-stu-id="8c6ee-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="8c6ee-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="8c6ee-249">PrintDialog</span></span>|  
|<span data-ttu-id="8c6ee-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-250">ProgressBar</span></span>|  
|<span data-ttu-id="8c6ee-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="8c6ee-251">RadioButton</span></span>|  
|<span data-ttu-id="8c6ee-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-252">RichTextBox</span></span>|  
|<span data-ttu-id="8c6ee-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="8c6ee-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="8c6ee-254">Scrollablecontrol</span><span class="sxs-lookup"><span data-stu-id="8c6ee-254">ScrollableControl</span></span>|  
|<span data-ttu-id="8c6ee-255">Soundplayer</span><span class="sxs-lookup"><span data-stu-id="8c6ee-255">SoundPlayer</span></span>|  
|<span data-ttu-id="8c6ee-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-256">StatusBar</span></span>|  
|<span data-ttu-id="8c6ee-257">Guias/página de guias</span><span class="sxs-lookup"><span data-stu-id="8c6ee-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="8c6ee-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-258">TextBox</span></span>|  
|<span data-ttu-id="8c6ee-259">Timer</span><span class="sxs-lookup"><span data-stu-id="8c6ee-259">Timer</span></span>|  
|<span data-ttu-id="8c6ee-260">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="8c6ee-260">Toolbar</span></span>|  
|<span data-ttu-id="8c6ee-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="8c6ee-261">ToolTip</span></span>|  
|<span data-ttu-id="8c6ee-262">Trackbar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-262">TrackBar</span></span>|  
|<span data-ttu-id="8c6ee-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="8c6ee-263">TreeView</span></span>|  
|<span data-ttu-id="8c6ee-264">Vscrollbar</span><span class="sxs-lookup"><span data-stu-id="8c6ee-264">VscrollBar</span></span>|  
|<span data-ttu-id="8c6ee-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8c6ee-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="8c6ee-266">Os controles a seguir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] são expostos apenas através de seu suporte para acessibilidade ativa da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="8c6ee-267">Algumas funcionalidades podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8c6ee-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="8c6ee-268">Nome do controle</span><span class="sxs-lookup"><span data-stu-id="8c6ee-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="8c6ee-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="8c6ee-269">BindingSource</span></span>|  
|<span data-ttu-id="8c6ee-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="8c6ee-270">DataGrid</span></span>|  
|<span data-ttu-id="8c6ee-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="8c6ee-271">DataGridView</span></span>|  
|<span data-ttu-id="8c6ee-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="8c6ee-272">DataNavigator</span></span>|  
|<span data-ttu-id="8c6ee-273">Domainupdown</span><span class="sxs-lookup"><span data-stu-id="8c6ee-273">DomainUpDown</span></span>|  
|<span data-ttu-id="8c6ee-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="8c6ee-274">ErrorProvider</span></span>|  
|<span data-ttu-id="8c6ee-275">Flowlayoutpanel</span><span class="sxs-lookup"><span data-stu-id="8c6ee-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="8c6ee-276">Formulário</span><span class="sxs-lookup"><span data-stu-id="8c6ee-276">Form</span></span>|  
|<span data-ttu-id="8c6ee-277">Linklabel</span><span class="sxs-lookup"><span data-stu-id="8c6ee-277">LinkLabel</span></span>|  
|<span data-ttu-id="8c6ee-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="8c6ee-278">HelpProvider</span></span>|  
|<span data-ttu-id="8c6ee-279">Maskedtextbox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="8c6ee-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8c6ee-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="8c6ee-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="8c6ee-281">NumericUpDown</span></span>|  
|<span data-ttu-id="8c6ee-282">Painel</span><span class="sxs-lookup"><span data-stu-id="8c6ee-282">Panel</span></span>|  
|<span data-ttu-id="8c6ee-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="8c6ee-283">PictureBox</span></span>|  
|<span data-ttu-id="8c6ee-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="8c6ee-284">PrintDocument</span></span>|  
|<span data-ttu-id="8c6ee-285">Controle de visualização de impressão</span><span class="sxs-lookup"><span data-stu-id="8c6ee-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="8c6ee-286">Impressãovisualização-caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="8c6ee-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="8c6ee-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="8c6ee-287">PropertyGrid</span></span>|  
|<span data-ttu-id="8c6ee-288">Usercontrol</span><span class="sxs-lookup"><span data-stu-id="8c6ee-288">UserControl</span></span>|  
|<span data-ttu-id="8c6ee-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8c6ee-289">ToolStrip</span></span>|  
|<span data-ttu-id="8c6ee-290">Tablelayoutpanel</span><span class="sxs-lookup"><span data-stu-id="8c6ee-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="8c6ee-291">Painel splitcontainer/splitter</span><span class="sxs-lookup"><span data-stu-id="8c6ee-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="8c6ee-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="8c6ee-292">Splitter</span></span>|  
|<span data-ttu-id="8c6ee-293">Container de rafting</span><span class="sxs-lookup"><span data-stu-id="8c6ee-293">RaftingContainer</span></span>|  
|<span data-ttu-id="8c6ee-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="8c6ee-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c6ee-295">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c6ee-295">See also</span></span>

- [<span data-ttu-id="8c6ee-296">Tipos de controle de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="8c6ee-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
