---
title: Implementando o padrão de controle TableItem de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 8f368fee6df6ebe5455f2029670e90f036d3d89a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932100"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="f57f4-102">Implementando o padrão de controle TableItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="f57f4-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f57f4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f57f4-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="f57f4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f57f4-105">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.ITableItemProvider>, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="f57f4-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="f57f4-106">Links para referências adicionais são listados no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="f57f4-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="f57f4-107">O <xref:System.Windows.Automation.TableItemPattern> padrão de controle é usado para dar suporte a controles filho de <xref:System.Windows.Automation.Provider.ITableProvider>contêineres que implementam o.</span><span class="sxs-lookup"><span data-stu-id="f57f4-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="f57f4-108">O acesso à funcionalidade de célula individual é fornecido pela implementação simultânea necessária do <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="f57f4-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="f57f4-109">Esse padrão de controle é análogo <xref:System.Windows.Automation.Provider.IGridItemProvider> à distinção que qualquer controle que implementa <xref:System.Windows.Automation.Provider.ITableItemProvider> deve expor de forma programática a relação entre a célula individual e suas informações de linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="f57f4-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="f57f4-110">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f57f4-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="f57f4-111">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="f57f4-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="f57f4-112">Para obter a funcionalidade de item de grade relacionada, consulte [implementando o padrão de controle GridItem de automação da interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="f57f4-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="f57f4-113">Membros necessários para ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="f57f4-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="f57f4-114">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="f57f4-114">Required member</span></span>|<span data-ttu-id="f57f4-115">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="f57f4-115">Member type</span></span>|<span data-ttu-id="f57f4-116">Observações</span><span class="sxs-lookup"><span data-stu-id="f57f4-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="f57f4-117">Método</span><span class="sxs-lookup"><span data-stu-id="f57f4-117">Method</span></span>|<span data-ttu-id="f57f4-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f57f4-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="f57f4-119">Método</span><span class="sxs-lookup"><span data-stu-id="f57f4-119">Method</span></span>|<span data-ttu-id="f57f4-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f57f4-120">None</span></span>|  
  
 <span data-ttu-id="f57f4-121">Este padrão de controle não tem propriedades ou eventos associados.</span><span class="sxs-lookup"><span data-stu-id="f57f4-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="f57f4-122">Exceções</span><span class="sxs-lookup"><span data-stu-id="f57f4-122">Exceptions</span></span>  
 <span data-ttu-id="f57f4-123">Este padrão de controle não tem nenhuma exceção associada.</span><span class="sxs-lookup"><span data-stu-id="f57f4-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57f4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f57f4-124">See also</span></span>

- [<span data-ttu-id="f57f4-125">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f57f4-126">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="f57f4-127">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="f57f4-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="f57f4-128">Implementando o padrão de controle Table de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="f57f4-129">Implementando o padrão de controle GridItem de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="f57f4-130">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="f57f4-131">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f57f4-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
