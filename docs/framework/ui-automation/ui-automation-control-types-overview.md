---
title: Visão Geral dos Tipos de Controle de Automação de Interface do Usuário
description: Leia uma visão geral dos tipos de controle de automação da interface do usuário, que são identificadores conhecidos que podem ser usados para indicar o tipo de controle que um elemento representa.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 204e950fca74c4f7bd2c13dc8a8891152954c071
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166136"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="969a5-103">Visão Geral dos Tipos de Controle de Automação de Interface do Usuário</span><span class="sxs-lookup"><span data-stu-id="969a5-103">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="969a5-104">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="969a5-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="969a5-105">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="969a5-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="969a5-106">os tipos de controle são identificadores bem conhecidos que podem ser usados para indicar que tipo de controle um determinado elemento representa, como uma caixa de combinação ou um botão.</span><span class="sxs-lookup"><span data-stu-id="969a5-106">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="969a5-107">Ter um identificador conhecido torna mais fácil para os dispositivos de tecnologia assistencial determinar quais tipos de controles estão disponíveis no [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] e como interagir com os controles.</span><span class="sxs-lookup"><span data-stu-id="969a5-107">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="969a5-108">Requisitos de tipo de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="969a5-108">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="969a5-109">os tipos de controle fornecem um conjunto de condições que os provedores devem atender.</span><span class="sxs-lookup"><span data-stu-id="969a5-109">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="969a5-110">Quando essas condições são atendidas, o controle pode usar o nome do tipo de controle específico.</span><span class="sxs-lookup"><span data-stu-id="969a5-110">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="969a5-111">Cada tipo de controle tem condições para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="969a5-111">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="969a5-112">padrões de controle – quais padrões de controle devem ter suporte, quais padrões de controle são opcionais e quais padrões de controle não devem ser suportados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="969a5-112">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="969a5-113">valores de propriedade — quais valores de propriedade têm suporte.</span><span class="sxs-lookup"><span data-stu-id="969a5-113">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="969a5-114">estrutura de árvore — a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore necessária para o controle.</span><span class="sxs-lookup"><span data-stu-id="969a5-114">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="969a5-115">Quando um controle atende às condições de um determinado tipo de controle, o <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> valor da propriedade indicará esse tipo de controle.</span><span class="sxs-lookup"><span data-stu-id="969a5-115">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="969a5-116">Tipos de controle de automação da interface do usuário atuais</span><span class="sxs-lookup"><span data-stu-id="969a5-116">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="969a5-117">A lista a seguir contém o conjunto atual de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tipos de controle:</span><span class="sxs-lookup"><span data-stu-id="969a5-117">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="969a5-118">Suporte de Automação de Interface de Usuário para o Tipo de Controle Button</span><span class="sxs-lookup"><span data-stu-id="969a5-118">UI Automation Support for the Button Control Type</span></span>](ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="969a5-119">Suporte de automação de interface de usuário para o Tipo de Controle Calendário</span><span class="sxs-lookup"><span data-stu-id="969a5-119">UI Automation Support for the Calendar Control Type</span></span>](ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="969a5-120">Suporte de automação de interface de usuário para o tipo de controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="969a5-120">UI Automation Support for the CheckBox Control Type</span></span>](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="969a5-121">Suporte de automação de interface de usuário para o tipo de controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="969a5-121">UI Automation Support for the ComboBox Control Type</span></span>](ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="969a5-122">Suporte de automação de interface de usuário para o tipo de controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="969a5-122">UI Automation Support for the DataGrid Control Type</span></span>](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="969a5-123">Suporte de automação de interface de usuário para o tipo de controle DataItem</span><span class="sxs-lookup"><span data-stu-id="969a5-123">UI Automation Support for the DataItem Control Type</span></span>](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="969a5-124">Suporte de automação de interface de usuário para o Tipo de Controle Document</span><span class="sxs-lookup"><span data-stu-id="969a5-124">UI Automation Support for the Document Control Type</span></span>](ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="969a5-125">Suporte de automação de interface de usuário para o Tipo de Controle Edit</span><span class="sxs-lookup"><span data-stu-id="969a5-125">UI Automation Support for the Edit Control Type</span></span>](ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="969a5-126">Suporte de automação de interface de usuário para o Tipo de Controle Grupo</span><span class="sxs-lookup"><span data-stu-id="969a5-126">UI Automation Support for the Group Control Type</span></span>](ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="969a5-127">Suporte de automação de interface de usuário para o Tipo de Controle Header</span><span class="sxs-lookup"><span data-stu-id="969a5-127">UI Automation Support for the Header Control Type</span></span>](ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="969a5-128">Suporte de automação de interface de usuário para o tipo de controle HeaderItem</span><span class="sxs-lookup"><span data-stu-id="969a5-128">UI Automation Support for the HeaderItem Control Type</span></span>](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="969a5-129">Suporte de automação de interface de usuário para o Tipo de Controle Hyperlink</span><span class="sxs-lookup"><span data-stu-id="969a5-129">UI Automation Support for the Hyperlink Control Type</span></span>](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="969a5-130">Suporte de automação de interface de usuário para o Tipo de Controle Image</span><span class="sxs-lookup"><span data-stu-id="969a5-130">UI Automation Support for the Image Control Type</span></span>](ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="969a5-131">Suporte de automação de interface do usuário para o tipo de controle List</span><span class="sxs-lookup"><span data-stu-id="969a5-131">UI Automation Support for the List Control Type</span></span>](ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="969a5-132">Suporte de automação de interface de usuário para o tipo de controle ListItem</span><span class="sxs-lookup"><span data-stu-id="969a5-132">UI Automation Support for the ListItem Control Type</span></span>](ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="969a5-133">Suporte de Automação de Interface de Usuário para o Tipo de Controle Menu</span><span class="sxs-lookup"><span data-stu-id="969a5-133">UI Automation Support for the Menu Control Type</span></span>](ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="969a5-134">Suporte de automação de interface de usuário para o tipo de controle MenuBar</span><span class="sxs-lookup"><span data-stu-id="969a5-134">UI Automation Support for the MenuBar Control Type</span></span>](ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="969a5-135">Suporte de automação de interface de usuário para o tipo de controle MenuItem</span><span class="sxs-lookup"><span data-stu-id="969a5-135">UI Automation Support for the MenuItem Control Type</span></span>](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="969a5-136">Suporte de automação de interface de usuário para o Tipo de Controle Pane</span><span class="sxs-lookup"><span data-stu-id="969a5-136">UI Automation Support for the Pane Control Type</span></span>](ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="969a5-137">Suporte de automação de interface de usuário para o tipo de controle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="969a5-137">UI Automation Support for the ProgressBar Control Type</span></span>](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="969a5-138">Suporte de automação de interface de usuário para o tipo de controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="969a5-138">UI Automation Support for the RadioButton Control Type</span></span>](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="969a5-139">Suporte de automação de interface de usuário para o tipo de controle ScrollBar</span><span class="sxs-lookup"><span data-stu-id="969a5-139">UI Automation Support for the ScrollBar Control Type</span></span>](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="969a5-140">Suporte de Automação de Interface de Usuário para o Tipo de Controle Separator</span><span class="sxs-lookup"><span data-stu-id="969a5-140">UI Automation Support for the Separator Control Type</span></span>](ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="969a5-141">Suporte de automação de interface de usuário para o Tipo de Controle Deslizante</span><span class="sxs-lookup"><span data-stu-id="969a5-141">UI Automation Support for the Slider Control Type</span></span>](ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="969a5-142">Suporte de automação de interface do usuário para o tipo de controle Spinner</span><span class="sxs-lookup"><span data-stu-id="969a5-142">UI Automation Support for the Spinner Control Type</span></span>](ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="969a5-143">Suporte de automação de interface de usuário para o tipo de controle SplitButton</span><span class="sxs-lookup"><span data-stu-id="969a5-143">UI Automation Support for the SplitButton Control Type</span></span>](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="969a5-144">Suporte de automação de interface de usuário para o tipo de controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="969a5-144">UI Automation Support for the StatusBar Control Type</span></span>](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="969a5-145">Suporte de automação de interface do usuário para o tipo de controle de tabela</span><span class="sxs-lookup"><span data-stu-id="969a5-145">UI Automation Support for the Tab Control Type</span></span>](ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="969a5-146">Suporte de automação de interface de usuário para o tipo de controle TabItem</span><span class="sxs-lookup"><span data-stu-id="969a5-146">UI Automation Support for the TabItem Control Type</span></span>](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="969a5-147">Suporte de Automação de Interface de Usuário para o Tipo de Controle de Tabela</span><span class="sxs-lookup"><span data-stu-id="969a5-147">UI Automation Support for the Table Control Type</span></span>](ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="969a5-148">Suporte da automação de interface do usuário para o tipo de controle Text</span><span class="sxs-lookup"><span data-stu-id="969a5-148">UI Automation Support for the Text Control Type</span></span>](ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="969a5-149">Suporte de automação de interface de usuário para o Tipo de Controle Thumb</span><span class="sxs-lookup"><span data-stu-id="969a5-149">UI Automation Support for the Thumb Control Type</span></span>](ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="969a5-150">Suporte de automação de interface de usuário para o tipo de controle TitleBar</span><span class="sxs-lookup"><span data-stu-id="969a5-150">UI Automation Support for the TitleBar Control Type</span></span>](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="969a5-151">Suporte de automação de interface de usuário para o tipo de controle ToolBar</span><span class="sxs-lookup"><span data-stu-id="969a5-151">UI Automation Support for the ToolBar Control Type</span></span>](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="969a5-152">Suporte de automação de interface de usuário para o tipo de controle ToolTip</span><span class="sxs-lookup"><span data-stu-id="969a5-152">UI Automation Support for the ToolTip Control Type</span></span>](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="969a5-153">Suporte de automação de interface de usuário para o Tipo de Controle Tree</span><span class="sxs-lookup"><span data-stu-id="969a5-153">UI Automation Support for the Tree Control Type</span></span>](ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="969a5-154">Suporte de automação de interface de usuário para o tipo de controle TreeItem</span><span class="sxs-lookup"><span data-stu-id="969a5-154">UI Automation Support for the TreeItem Control Type</span></span>](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="969a5-155">Suporte de Automação de Interface de Usuário para o Tipo de Controle Window</span><span class="sxs-lookup"><span data-stu-id="969a5-155">UI Automation Support for the Window Control Type</span></span>](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="969a5-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="969a5-156">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
