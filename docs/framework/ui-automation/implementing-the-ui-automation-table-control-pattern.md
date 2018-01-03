---
title: "Implementando o padrão de controle de tabela de automação de interface de usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1e0b3c09948b53363888ae133cd0c4d9f9ae8f05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="d30a4-102">Implementando o padrão de controle de tabela de automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d30a4-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d30a4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d30a4-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="d30a4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d30a4-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ITableProvider>, incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="d30a4-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="d30a4-106">Links para referências adicionais são listadas no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="d30a4-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="d30a4-107">O <xref:System.Windows.Automation.TablePattern> padrão de controle é usado para oferecer suporte aos controles que atuam como contêineres para uma coleção de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="d30a4-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="d30a4-108">Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ITableItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser percorrido por linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="d30a4-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="d30a4-109">Esse padrão de controle é análogo a <xref:System.Windows.Automation.Provider.IGridProvider>, com a diferença que qualquer controle implementando <xref:System.Windows.Automation.Provider.ITableProvider> também deve expor uma relação de cabeçalho de coluna e/ou linha para cada elemento filho.</span><span class="sxs-lookup"><span data-stu-id="d30a4-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="d30a4-110">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d30a4-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d30a4-111">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="d30a4-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d30a4-112">Ao implementar o padrão de controle de tabela, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="d30a4-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d30a4-113">Acesso ao conteúdo das células individuais é por meio de um sistema de coordenadas bidimensional lógico ou matriz fornecida pela implementação simultânea necessária de <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="d30a4-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
-   <span data-ttu-id="d30a4-114">Um cabeçalho de coluna ou linha pode estar contido em um objeto de tabela ou ser um objeto separado de cabeçalho que está associado um objeto de tabela.</span><span class="sxs-lookup"><span data-stu-id="d30a4-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
-   <span data-ttu-id="d30a4-115">Cabeçalhos de coluna e linha podem incluir um cabeçalho principal, bem como os cabeçalhos de suporte.</span><span class="sxs-lookup"><span data-stu-id="d30a4-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d30a4-116">Esse conceito fica evidente em uma [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilha em que um usuário tenha definido uma coluna "Nome".</span><span class="sxs-lookup"><span data-stu-id="d30a4-116">This concept becomes evident in a [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="d30a4-117">Esta coluna agora tem dois cabeçalhos — o cabeçalho de "Nome" definido pelo usuário e a designação alfanumérica para aquela coluna atribuída pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d30a4-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
-   <span data-ttu-id="d30a4-118">Consulte [Implementando o padrão de controle Grid de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) para a funcionalidade de grade relacionados.</span><span class="sxs-lookup"><span data-stu-id="d30a4-118">See [Implementing the UI Automation Grid Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="d30a4-119">![Tabela com itens de cabeçalho complexos. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="d30a4-119">![Table with complex header items.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="d30a4-120">Exemplo de uma tabela com cabeçalhos de coluna complexa</span><span class="sxs-lookup"><span data-stu-id="d30a4-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="d30a4-121">![Tabela com RowOrColumnMajor ambíguas. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="d30a4-121">![Table with ambiguous RowOrColumnMajor property.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="d30a4-122">Exemplo de uma tabela com RowOrColumnMajor ambíguas</span><span class="sxs-lookup"><span data-stu-id="d30a4-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="d30a4-123">Membros necessários para IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="d30a4-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="d30a4-124">As propriedades e métodos a seguir são necessários para a interface ITableProvider.</span><span class="sxs-lookup"><span data-stu-id="d30a4-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="d30a4-125">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="d30a4-125">Required members</span></span>|<span data-ttu-id="d30a4-126">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="d30a4-126">Member type</span></span>|<span data-ttu-id="d30a4-127">Observações</span><span class="sxs-lookup"><span data-stu-id="d30a4-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="d30a4-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d30a4-128">Property</span></span>|<span data-ttu-id="d30a4-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d30a4-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="d30a4-130">Método</span><span class="sxs-lookup"><span data-stu-id="d30a4-130">Method</span></span>|<span data-ttu-id="d30a4-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d30a4-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="d30a4-132">Método</span><span class="sxs-lookup"><span data-stu-id="d30a4-132">Method</span></span>|<span data-ttu-id="d30a4-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d30a4-133">None</span></span>|  
  
 <span data-ttu-id="d30a4-134">Esse padrão de controle não possui eventos associados.</span><span class="sxs-lookup"><span data-stu-id="d30a4-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d30a4-135">Exceções</span><span class="sxs-lookup"><span data-stu-id="d30a4-135">Exceptions</span></span>  
 <span data-ttu-id="d30a4-136">Esse padrão de controle não tem exceção associada.</span><span class="sxs-lookup"><span data-stu-id="d30a4-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30a4-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d30a4-137">See Also</span></span>  
 [<span data-ttu-id="d30a4-138">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="d30a4-139">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="d30a4-140">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="d30a4-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="d30a4-141">Implementando o padrão de controle TableItem de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-141">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="d30a4-142">Implementando o padrão de controle Grid de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-142">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="d30a4-143">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-143">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="d30a4-144">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d30a4-144">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
