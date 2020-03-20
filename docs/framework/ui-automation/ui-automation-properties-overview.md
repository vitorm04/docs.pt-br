---
title: Visão geral das propriedades de automação da interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 8a44fd89017002ae51d9b15a22bac97668d0ff90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179865"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="873fb-102">Visão geral das propriedades de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="873fb-102">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="873fb-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="873fb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="873fb-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="873fb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="873fb-105">Os provedores de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] automação de ui expõem propriedades em elementos.</span><span class="sxs-lookup"><span data-stu-id="873fb-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="873fb-106">Essas propriedades permitem que os aplicativos clientes de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]automação de interface do usuário descubram informações sobre peças dos controles, especialmente os da statice e dinâmica.</span><span class="sxs-lookup"><span data-stu-id="873fb-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="873fb-107">Esta seção dá uma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ampla visão geral das propriedades.</span><span class="sxs-lookup"><span data-stu-id="873fb-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="873fb-108">Informações mais específicas são fornecidas nos seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="873fb-108">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="873fb-109">Automação de Propriedades de Interface de Usuário para Clientes.</span><span class="sxs-lookup"><span data-stu-id="873fb-109">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="873fb-110">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="873fb-110">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a><span data-ttu-id="873fb-111">Identificadores de propriedades</span><span class="sxs-lookup"><span data-stu-id="873fb-111">Property Identifiers</span></span>  
 <span data-ttu-id="873fb-112">Cada propriedade é identificada por um número e um nome.</span><span class="sxs-lookup"><span data-stu-id="873fb-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="873fb-113">Os nomes das propriedades são usados apenas para depuração e diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="873fb-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="873fb-114">Os provedores usam os IDs numéricos para identificar solicitações de propriedade recebidas.</span><span class="sxs-lookup"><span data-stu-id="873fb-114">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="873fb-115">Os aplicativos cliente, no <xref:System.Windows.Automation.AutomationProperty>entanto, só usam , o que encapsula o número e o nome, para identificar propriedades que desejam recuperar.</span><span class="sxs-lookup"><span data-stu-id="873fb-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="873fb-116"><xref:System.Windows.Automation.AutomationProperty>objetos que representam propriedades particulares estão disponíveis como campos em várias classes.</span><span class="sxs-lookup"><span data-stu-id="873fb-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="873fb-117">Por razões de segurança, os provedores de automação de ui obtêm esses objetos de um conjunto separado de classes que estão contidos em Uiautomationtypes.dll.</span><span class="sxs-lookup"><span data-stu-id="873fb-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="873fb-118">A tabela a seguir categoriza as <xref:System.Windows.Automation.AutomationProperty>propriedades pelas classes que contêm os IDs.</span><span class="sxs-lookup"><span data-stu-id="873fb-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="873fb-119">Tipos de propriedades</span><span class="sxs-lookup"><span data-stu-id="873fb-119">Kinds of properties</span></span>|<span data-ttu-id="873fb-120">Os clientes obtêm ids de</span><span class="sxs-lookup"><span data-stu-id="873fb-120">Clients get IDs from</span></span>|<span data-ttu-id="873fb-121">Provedores obtêm IDs de</span><span class="sxs-lookup"><span data-stu-id="873fb-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="873fb-122">Propriedades comuns a todos os elementos (ver tabelas a seguir)</span><span class="sxs-lookup"><span data-stu-id="873fb-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="873fb-123">Posição de uma janela de acoplamento</span><span class="sxs-lookup"><span data-stu-id="873fb-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="873fb-124">Estado de um elemento que pode expandir e colapsar</span><span class="sxs-lookup"><span data-stu-id="873fb-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="873fb-125">Propriedades de um item em uma grade</span><span class="sxs-lookup"><span data-stu-id="873fb-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="873fb-126">Propriedades de uma grade</span><span class="sxs-lookup"><span data-stu-id="873fb-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="873fb-127">Visão atual e suportada de um elemento que tem múltiplas visualizações</span><span class="sxs-lookup"><span data-stu-id="873fb-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="873fb-128">Propriedades de um elemento que se move sobre uma gama de valores, como um controle deslizante</span><span class="sxs-lookup"><span data-stu-id="873fb-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="873fb-129">Propriedades de uma janela de rolagem</span><span class="sxs-lookup"><span data-stu-id="873fb-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="873fb-130">Status e contêiner de um item que pode ser selecionado, como em uma lista</span><span class="sxs-lookup"><span data-stu-id="873fb-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="873fb-131">Propriedades de um controle que contém itens de seleção</span><span class="sxs-lookup"><span data-stu-id="873fb-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="873fb-132">Cabeçalhos de coluna e linha de um item em uma tabela</span><span class="sxs-lookup"><span data-stu-id="873fb-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="873fb-133">Cabeçalhos de coluna e linha, e orientação, de uma tabela</span><span class="sxs-lookup"><span data-stu-id="873fb-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="873fb-134">Estado de um controle alternado</span><span class="sxs-lookup"><span data-stu-id="873fb-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="873fb-135">Capacidades de um elemento que pode ser movido, girado ou redimensionado</span><span class="sxs-lookup"><span data-stu-id="873fb-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="873fb-136">Valor e recursos de leitura/gravação de um elemento que tem um valor</span><span class="sxs-lookup"><span data-stu-id="873fb-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="873fb-137">Capacidades e estado de uma janela</span><span class="sxs-lookup"><span data-stu-id="873fb-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a><span data-ttu-id="873fb-138">Propriedades por Categoria</span><span class="sxs-lookup"><span data-stu-id="873fb-138">Properties by Category</span></span>  
 <span data-ttu-id="873fb-139">As tabelas a seguir categorizam as <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElementIdentifiers>propriedades em que as ids são encontradas e .</span><span class="sxs-lookup"><span data-stu-id="873fb-139">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="873fb-140">Essas propriedades são comuns a todos os controles.</span><span class="sxs-lookup"><span data-stu-id="873fb-140">These properties are common to all controls.</span></span> <span data-ttu-id="873fb-141">Todos, exceto alguns deles, provavelmente estarão estáticos ao longo da vida útil da aplicação do provedor; a maioria das propriedades dinâmicas estão associadas a padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="873fb-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="873fb-142">A coluna **Acesso ao Imóvel** lista quaisquer outros <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> acessórios <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>para cada propriedade, além de e .</span><span class="sxs-lookup"><span data-stu-id="873fb-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="873fb-143">Para obter mais informações sobre como obter propriedades em um aplicativo cliente, consulte [Propriedades de automação de interface do usuário para clientes](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="873fb-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="873fb-144">Para obter informações específicas sobre cada propriedade, siga o link na coluna **Acesso à Propriedade.**</span><span class="sxs-lookup"><span data-stu-id="873fb-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="873fb-145">Exibir Características</span><span class="sxs-lookup"><span data-stu-id="873fb-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="873fb-146">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-146">Property identifier</span></span>|<span data-ttu-id="873fb-147">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="873fb-148">n/d</span><span class="sxs-lookup"><span data-stu-id="873fb-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="873fb-149">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="873fb-149">Element Type</span></span>  
  
|<span data-ttu-id="873fb-150">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-150">Property identifier</span></span>|<span data-ttu-id="873fb-151">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="873fb-152">Identificação</span><span class="sxs-lookup"><span data-stu-id="873fb-152">Identification</span></span>  
  
|<span data-ttu-id="873fb-153">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-153">Property identifier</span></span>|<span data-ttu-id="873fb-154">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="873fb-155">Interação</span><span class="sxs-lookup"><span data-stu-id="873fb-155">Interaction</span></span>  
  
|<span data-ttu-id="873fb-156">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-156">Property identifier</span></span>|<span data-ttu-id="873fb-157">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="873fb-158">Suporte para Padrões</span><span class="sxs-lookup"><span data-stu-id="873fb-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="873fb-159">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-159">Property identifier</span></span>|<span data-ttu-id="873fb-160">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-160">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="873fb-161">Diversos</span><span class="sxs-lookup"><span data-stu-id="873fb-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="873fb-162">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-162">Property identifier</span></span>|<span data-ttu-id="873fb-163">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a><span data-ttu-id="873fb-164">Localização</span><span class="sxs-lookup"><span data-stu-id="873fb-164">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="873fb-165">os provedores devem apresentar as seguintes propriedades na linguagem do sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="873fb-165">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a><span data-ttu-id="873fb-166">Propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="873fb-166">Properties and Events</span></span>  
 <span data-ttu-id="873fb-167">Intimamente ligado com as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades em é o conceito de eventos alterados de propriedade.</span><span class="sxs-lookup"><span data-stu-id="873fb-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="873fb-168">Para propriedades dinâmicas, o aplicativo cliente precisa de uma maneira de saber que um valor de propriedade mudou, para que ele possa atualizar seu cache de informações ou reagir às novas informações de alguma outra forma.</span><span class="sxs-lookup"><span data-stu-id="873fb-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="873fb-169">Os provedores levantam [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] eventos quando algo nas mudanças.</span><span class="sxs-lookup"><span data-stu-id="873fb-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="873fb-170">Por exemplo, se uma caixa de seleção for selecionada ou limpa, um evento alterado por propriedade será levantado pela implementação do padrão Alternar pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="873fb-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="873fb-171">Os provedores podem levantar eventos seletivamente, dependendo se algum cliente está ouvindo eventos ou ouvindo eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="873fb-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="873fb-172">Nem todas as alterações de propriedade levantam eventos; que depende inteiramente da implementação do provedor de Automação de IU para o elemento.</span><span class="sxs-lookup"><span data-stu-id="873fb-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="873fb-173">Por exemplo, os provedores proxy padrão para caixas <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> de lista não levantam um evento quando as alterações.</span><span class="sxs-lookup"><span data-stu-id="873fb-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="873fb-174">Neste caso, a aplicação deve, <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>em vez disso, ouvir um .</span><span class="sxs-lookup"><span data-stu-id="873fb-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="873fb-175">Os clientes ouvem os eventos assinando-os.</span><span class="sxs-lookup"><span data-stu-id="873fb-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="873fb-176">Subscrever eventos significa criar métodos de delegação que possam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lidar com os eventos e, em seguida, passar os métodos para juntamente com os eventos específicos que serão tratados nesses métodos.</span><span class="sxs-lookup"><span data-stu-id="873fb-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="873fb-177">Para eventos alterados por propriedade, <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>em particular, os clientes devem implementar .</span><span class="sxs-lookup"><span data-stu-id="873fb-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873fb-178">Confira também</span><span class="sxs-lookup"><span data-stu-id="873fb-178">See also</span></span>

- [<span data-ttu-id="873fb-179">Armazenando em cache em clientes de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="873fb-179">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="873fb-180">Automação de Propriedades de Interface de Usuário para Clientes.</span><span class="sxs-lookup"><span data-stu-id="873fb-180">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="873fb-181">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="873fb-181">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="873fb-182">Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="873fb-182">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="873fb-183">Retornando Propriedades de um Provedor de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="873fb-183">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="873fb-184">Disparar Eventos de um Provedor de Automação UI</span><span class="sxs-lookup"><span data-stu-id="873fb-184">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
