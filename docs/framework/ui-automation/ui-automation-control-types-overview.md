---
title: Visão Geral dos Tipos de Controle de Automação de Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 5274a2a090669a9c51c5247b68d2b0460625a494
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911566"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="1261a-102">Visão Geral dos Tipos de Controle de Automação de Interface do Usuário</span><span class="sxs-lookup"><span data-stu-id="1261a-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="1261a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="1261a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1261a-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1261a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="1261a-105">os tipos de controle são identificadores bem conhecidos que podem ser usados para indicar que tipo de controle um determinado elemento representa, como uma caixa de combinação ou um botão.</span><span class="sxs-lookup"><span data-stu-id="1261a-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="1261a-106">Ter um identificador conhecido torna mais fácil para os dispositivos de tecnologia assistencial determinar quais tipos de controles estão disponíveis no [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] e como interagir com os controles.</span><span class="sxs-lookup"><span data-stu-id="1261a-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="1261a-107">Requisitos de tipo de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1261a-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="1261a-108">os tipos de controle fornecem um conjunto de condições que os provedores devem atender.</span><span class="sxs-lookup"><span data-stu-id="1261a-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="1261a-109">Quando essas condições são atendidas, o controle pode usar o nome do tipo de controle específico.</span><span class="sxs-lookup"><span data-stu-id="1261a-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="1261a-110">Cada tipo de controle tem condições para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1261a-110">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1261a-111">padrões de controle – quais padrões de controle devem ter suporte, quais padrões de controle são opcionais e quais padrões de controle não devem ser suportados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="1261a-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1261a-112">valores de propriedade — quais valores de propriedade têm suporte.</span><span class="sxs-lookup"><span data-stu-id="1261a-112">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1261a-113">estrutura de árvore — a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore necessária para o controle.</span><span class="sxs-lookup"><span data-stu-id="1261a-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="1261a-114">Quando um controle atende às condições de um determinado tipo de controle, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> o valor da propriedade indicará esse tipo de controle.</span><span class="sxs-lookup"><span data-stu-id="1261a-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="1261a-115">Tipos de controle de automação da interface do usuário atuais</span><span class="sxs-lookup"><span data-stu-id="1261a-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="1261a-116">A lista a seguir contém o conjunto atual [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] de tipos de controle:</span><span class="sxs-lookup"><span data-stu-id="1261a-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="1261a-117">Suporte de automação de interface do usuário para o tipo de controle de botão</span><span class="sxs-lookup"><span data-stu-id="1261a-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="1261a-118">Suporte de automação de interface do usuário para o tipo de controle de Calendar</span><span class="sxs-lookup"><span data-stu-id="1261a-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="1261a-119">Suporte de automação de interface do usuário para o tipo de controle de CheckBox</span><span class="sxs-lookup"><span data-stu-id="1261a-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="1261a-120">Suporte de automação de interface do usuário para o tipo de controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="1261a-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="1261a-121">Suporte de automação de interface do usuário para o tipo de controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="1261a-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="1261a-122">Suporte de automação de interface do usuário para o tipo de controle DataItem</span><span class="sxs-lookup"><span data-stu-id="1261a-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="1261a-123">Suporte de automação de interface do usuário para o tipo de controle Document</span><span class="sxs-lookup"><span data-stu-id="1261a-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="1261a-124">Suporte de automação de interface do usuário para o tipo de controle de edição</span><span class="sxs-lookup"><span data-stu-id="1261a-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="1261a-125">Suporte de automação de interface do usuário para o tipo de controle Group</span><span class="sxs-lookup"><span data-stu-id="1261a-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="1261a-126">Suporte de automação de interface do usuário para o tipo de controle Header</span><span class="sxs-lookup"><span data-stu-id="1261a-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="1261a-127">Suporte de automação de interface do usuário para o tipo de controle HeaderItem</span><span class="sxs-lookup"><span data-stu-id="1261a-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="1261a-128">Suporte de automação de interface do usuário para o tipo de controle Hyperlink</span><span class="sxs-lookup"><span data-stu-id="1261a-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="1261a-129">Suporte de automação de interface do usuário para o tipo de controle de imagem</span><span class="sxs-lookup"><span data-stu-id="1261a-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="1261a-130">Suporte de automação de interface do usuário para o tipo de controle de lista</span><span class="sxs-lookup"><span data-stu-id="1261a-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="1261a-131">Suporte de automação de interface do usuário para o tipo de controle ListItem</span><span class="sxs-lookup"><span data-stu-id="1261a-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="1261a-132">Suporte de automação de interface do usuário para o tipo de controle Menu</span><span class="sxs-lookup"><span data-stu-id="1261a-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="1261a-133">Suporte de automação de interface do usuário para o tipo de controle MenuBar</span><span class="sxs-lookup"><span data-stu-id="1261a-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="1261a-134">Suporte de automação de interface do usuário para o tipo de controle MenuItem</span><span class="sxs-lookup"><span data-stu-id="1261a-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="1261a-135">Suporte de automação de interface do usuário para o tipo de controle de painel</span><span class="sxs-lookup"><span data-stu-id="1261a-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="1261a-136">Suporte de automação de interface do usuário para o tipo de controle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="1261a-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="1261a-137">Suporte de automação de interface do usuário para o tipo de controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="1261a-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="1261a-138">Suporte de automação de interface do usuário para o tipo de controle ScrollBar</span><span class="sxs-lookup"><span data-stu-id="1261a-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="1261a-139">Suporte de automação de interface do usuário para o tipo de controle Separator</span><span class="sxs-lookup"><span data-stu-id="1261a-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="1261a-140">Suporte de automação de interface do usuário para o tipo de controle deslizante</span><span class="sxs-lookup"><span data-stu-id="1261a-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="1261a-141">Suporte de automação de interface do usuário para o tipo de controle Spinner</span><span class="sxs-lookup"><span data-stu-id="1261a-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="1261a-142">Suporte de automação de interface do usuário para o tipo de controle SplitButton</span><span class="sxs-lookup"><span data-stu-id="1261a-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="1261a-143">Suporte de automação de interface do usuário para o tipo de controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="1261a-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="1261a-144">Suporte de automação de interface do usuário para o tipo de controle guia</span><span class="sxs-lookup"><span data-stu-id="1261a-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="1261a-145">Suporte de automação de interface do usuário para o tipo de controle TabItem</span><span class="sxs-lookup"><span data-stu-id="1261a-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="1261a-146">Suporte de automação de interface do usuário para o tipo de controle Table</span><span class="sxs-lookup"><span data-stu-id="1261a-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="1261a-147">Suporte de automação de interface do usuário para o tipo de controle Text</span><span class="sxs-lookup"><span data-stu-id="1261a-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="1261a-148">Suporte de automação de interface do usuário para o tipo de controle de posição</span><span class="sxs-lookup"><span data-stu-id="1261a-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="1261a-149">Suporte de automação de interface do usuário para o tipo de controle TitleBar</span><span class="sxs-lookup"><span data-stu-id="1261a-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="1261a-150">Suporte de automação de interface do usuário para o tipo de controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="1261a-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="1261a-151">Suporte de automação de interface do usuário para o tipo de controle ToolTip</span><span class="sxs-lookup"><span data-stu-id="1261a-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="1261a-152">Suporte de automação de interface do usuário para o tipo de controle Tree</span><span class="sxs-lookup"><span data-stu-id="1261a-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="1261a-153">Suporte de automação de interface do usuário para o tipo de controle TreeItem</span><span class="sxs-lookup"><span data-stu-id="1261a-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="1261a-154">Suporte de automação de interface do usuário para o tipo de controle Window</span><span class="sxs-lookup"><span data-stu-id="1261a-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="1261a-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1261a-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
