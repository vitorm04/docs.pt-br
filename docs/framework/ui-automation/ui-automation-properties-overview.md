---
title: Visão geral das propriedades de automação da interface do usuário
description: Veja uma ampla visão geral das propriedades de automação da interface do usuário da Microsoft. Saiba mais sobre identificadores de propriedade, propriedades por categoria, localização, propriedades e eventos.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 17d780c059530be8c91890302ea4066de2d4aa73
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163211"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="ac1a9-104">Visão geral das propriedades de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ac1a9-104">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="ac1a9-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ac1a9-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="ac1a9-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="ac1a9-107">Provedores de automação de interface do usuário expõem propriedades em [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementos.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-107">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="ac1a9-108">Essas propriedades permitem que aplicativos cliente de automação da interface do usuário descubram informações sobre partes do [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , especialmente controles, incluindo dados estáticos e dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-108">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="ac1a9-109">Esta seção fornece uma ampla visão geral das [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Propriedades.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-109">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="ac1a9-110">Informações mais específicas são fornecidas nos seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="ac1a9-110">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="ac1a9-111">Automação de Propriedades de Interface de Usuário para Clientes.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-111">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="ac1a9-112">Implementação do provedor de automação de interface do usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="ac1a9-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a><span data-ttu-id="ac1a9-113">Identificadores de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-113">Property Identifiers</span></span>  
 <span data-ttu-id="ac1a9-114">Cada propriedade é identificada por um número e um nome.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-114">Every property is identified by a number and a name.</span></span> <span data-ttu-id="ac1a9-115">Os nomes das propriedades são usados somente para depuração e diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-115">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="ac1a9-116">Os provedores usam as IDs numéricas para identificar as solicitações de propriedade de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-116">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="ac1a9-117">No entanto, os aplicativos cliente usam apenas <xref:System.Windows.Automation.AutomationProperty> o, que encapsula o número e o nome, para identificar as propriedades que desejam recuperar.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-117">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="ac1a9-118"><xref:System.Windows.Automation.AutomationProperty>objetos que representam propriedades específicas estão disponíveis como campos em várias classes.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-118"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="ac1a9-119">Por motivos de segurança, os provedores de automação da interface do usuário obtêm esses objetos de um conjunto separado de classes contidas no Uiautomationtypes.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-119">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="ac1a9-120">A tabela a seguir categoriza as propriedades pelas classes que contêm as <xref:System.Windows.Automation.AutomationProperty> IDs.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-120">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="ac1a9-121">Tipos de propriedades</span><span class="sxs-lookup"><span data-stu-id="ac1a9-121">Kinds of properties</span></span>|<span data-ttu-id="ac1a9-122">Clientes obtêm IDs de</span><span class="sxs-lookup"><span data-stu-id="ac1a9-122">Clients get IDs from</span></span>|<span data-ttu-id="ac1a9-123">Os provedores obtêm IDs de</span><span class="sxs-lookup"><span data-stu-id="ac1a9-123">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="ac1a9-124">Propriedades comuns a todos os elementos (consulte as tabelas a seguir)</span><span class="sxs-lookup"><span data-stu-id="ac1a9-124">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="ac1a9-125">Posição de uma janela de encaixe</span><span class="sxs-lookup"><span data-stu-id="ac1a9-125">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-126">Estado de um elemento que pode ser expandido e recolhido</span><span class="sxs-lookup"><span data-stu-id="ac1a9-126">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="ac1a9-127">Propriedades de um item em uma grade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-127">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-128">Propriedades de uma grade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-128">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-129">Exibição atual e com suporte de um elemento que tem várias exibições</span><span class="sxs-lookup"><span data-stu-id="ac1a9-129">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-130">Propriedades de um elemento que se movem sobre um intervalo de valores, como um controle deslizante</span><span class="sxs-lookup"><span data-stu-id="ac1a9-130">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="ac1a9-131">Propriedades de uma janela de rolagem</span><span class="sxs-lookup"><span data-stu-id="ac1a9-131">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-132">Status e contêiner de um item que pode ser selecionado, como em uma lista</span><span class="sxs-lookup"><span data-stu-id="ac1a9-132">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-133">Propriedades de um controle que contém itens de seleção</span><span class="sxs-lookup"><span data-stu-id="ac1a9-133">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-134">Cabeçalhos de coluna e linha de um item em uma tabela</span><span class="sxs-lookup"><span data-stu-id="ac1a9-134">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-135">Cabeçalhos de coluna e linha e orientação de uma tabela</span><span class="sxs-lookup"><span data-stu-id="ac1a9-135">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="ac1a9-136">Estado de um controle de alternância</span><span class="sxs-lookup"><span data-stu-id="ac1a9-136">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="ac1a9-137">Recursos de um elemento que podem ser movidos, girados ou redimensionados</span><span class="sxs-lookup"><span data-stu-id="ac1a9-137">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="ac1a9-138">Recursos de valor e leitura/gravação de um elemento que tem um valor</span><span class="sxs-lookup"><span data-stu-id="ac1a9-138">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="ac1a9-139">Recursos e estado de uma janela</span><span class="sxs-lookup"><span data-stu-id="ac1a9-139">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a><span data-ttu-id="ac1a9-140">Propriedades por Categoria</span><span class="sxs-lookup"><span data-stu-id="ac1a9-140">Properties by Category</span></span>  
 <span data-ttu-id="ac1a9-141">As tabelas a seguir categorizam as propriedades cujas IDs são encontradas em <xref:System.Windows.Automation.AutomationElement> e <xref:System.Windows.Automation.AutomationElementIdentifiers> .</span><span class="sxs-lookup"><span data-stu-id="ac1a9-141">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="ac1a9-142">Essas propriedades são comuns a todos os controles.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-142">These properties are common to all controls.</span></span> <span data-ttu-id="ac1a9-143">Todos os poucos deles provavelmente serão estáticos durante o tempo de vida do aplicativo do provedor; a maioria das propriedades dinâmicas está associada aos padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-143">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="ac1a9-144">A coluna **acesso à propriedade** lista quaisquer outros acessadores para cada propriedade, além <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> de <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> e.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-144">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="ac1a9-145">Para obter mais informações sobre como obter propriedades em um aplicativo cliente, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ac1a9-145">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac1a9-146">Para obter informações específicas sobre cada propriedade, siga o link na coluna **acesso à propriedade** .</span><span class="sxs-lookup"><span data-stu-id="ac1a9-146">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="ac1a9-147">Exibir Características</span><span class="sxs-lookup"><span data-stu-id="ac1a9-147">Display Characteristics</span></span>  
  
|<span data-ttu-id="ac1a9-148">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-148">Property identifier</span></span>|<span data-ttu-id="ac1a9-149">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-149">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="ac1a9-150">N/D</span><span class="sxs-lookup"><span data-stu-id="ac1a9-150">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="ac1a9-151">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="ac1a9-151">Element Type</span></span>  
  
|<span data-ttu-id="ac1a9-152">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-152">Property identifier</span></span>|<span data-ttu-id="ac1a9-153">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-153">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="ac1a9-154">Identificação</span><span class="sxs-lookup"><span data-stu-id="ac1a9-154">Identification</span></span>  
  
|<span data-ttu-id="ac1a9-155">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-155">Property identifier</span></span>|<span data-ttu-id="ac1a9-156">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-156">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="ac1a9-157">Interação</span><span class="sxs-lookup"><span data-stu-id="ac1a9-157">Interaction</span></span>  
  
|<span data-ttu-id="ac1a9-158">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-158">Property identifier</span></span>|<span data-ttu-id="ac1a9-159">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-159">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="ac1a9-160">Suporte para padrões</span><span class="sxs-lookup"><span data-stu-id="ac1a9-160">Support for Patterns</span></span>  
  
|<span data-ttu-id="ac1a9-161">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-161">Property identifier</span></span>|<span data-ttu-id="ac1a9-162">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-162">Property access</span></span>|  
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
  
### <a name="miscellaneous"></a><span data-ttu-id="ac1a9-163">Diversos</span><span class="sxs-lookup"><span data-stu-id="ac1a9-163">Miscellaneous</span></span>  
  
|<span data-ttu-id="ac1a9-164">Identificador de propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-164">Property identifier</span></span>|<span data-ttu-id="ac1a9-165">Acesso à propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-165">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a><span data-ttu-id="ac1a9-166">Localização</span><span class="sxs-lookup"><span data-stu-id="ac1a9-166">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="ac1a9-167">os provedores devem apresentar as seguintes propriedades no idioma do sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="ac1a9-167">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a><span data-ttu-id="ac1a9-168">Propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="ac1a9-168">Properties and Events</span></span>  
 <span data-ttu-id="ac1a9-169">Fortemente vinculados com as propriedades no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é o conceito de eventos de alteração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-169">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="ac1a9-170">Para propriedades dinâmicas, o aplicativo cliente precisa de uma maneira de saber que um valor de propriedade foi alterado, para que ele possa atualizar seu cache de informações ou reagir às novas informações de alguma outra maneira.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-170">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="ac1a9-171">Provedores geram eventos quando algo nas [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] alterações.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-171">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="ac1a9-172">Por exemplo, se uma caixa de seleção for marcada ou desmarcada, um evento de alteração de propriedade será gerado pela implementação do provedor do padrão de alternância.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-172">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="ac1a9-173">Os provedores podem gerar eventos seletivamente, dependendo se algum cliente está ouvindo eventos ou escutando eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-173">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="ac1a9-174">Nem todas as alterações de propriedade geram eventos; Isso é inteiramente a implementação do provedor de automação da interface do usuário para o elemento.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-174">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="ac1a9-175">Por exemplo, os provedores de proxy padrão para caixas de listagem não geram um evento quando as <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> alterações.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-175">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="ac1a9-176">Nesse caso, o aplicativo deve escutar um <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent> .</span><span class="sxs-lookup"><span data-stu-id="ac1a9-176">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="ac1a9-177">Os clientes escutam eventos assinando-os.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-177">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="ac1a9-178">Assinar eventos significa criar métodos delegados que possam manipular os eventos e, em seguida, passar os métodos para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] junto com os eventos específicos que serão tratados nesses métodos.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-178">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="ac1a9-179">Para eventos de propriedade alterada em particular, os clientes devem implementar <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="ac1a9-179">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1a9-180">Confira também</span><span class="sxs-lookup"><span data-stu-id="ac1a9-180">See also</span></span>

- [<span data-ttu-id="ac1a9-181">Armazenando em cache em clientes de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ac1a9-181">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="ac1a9-182">Automação de Propriedades de Interface de Usuário para Clientes.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-182">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="ac1a9-183">Implementação do provedor de automação de interface do usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="ac1a9-183">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="ac1a9-184">Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="ac1a9-184">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="ac1a9-185">Retornando Propriedades de um Provedor de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="ac1a9-185">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="ac1a9-186">Disparar Eventos de um Provedor de Automação UI</span><span class="sxs-lookup"><span data-stu-id="ac1a9-186">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
