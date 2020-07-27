---
title: Implementando o padrão de controle TableItem de interface de usuário
description: Examine as diretrizes e convenções para implementar o padrão de controle TableItem na automação da interface do usuário. Conheça os membros necessários para a interface ITableItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3d6d31fe0e041fbba147df14d290a775188755f2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163515"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="68bc1-104">Implementando o padrão de controle TableItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-104">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="68bc1-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="68bc1-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="68bc1-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="68bc1-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="68bc1-107">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.ITableItemProvider> , incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="68bc1-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="68bc1-108">Links para referências adicionais são listados no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="68bc1-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="68bc1-109">O <xref:System.Windows.Automation.TableItemPattern> padrão de controle é usado para dar suporte a controles filho de contêineres que implementam o <xref:System.Windows.Automation.Provider.ITableProvider> .</span><span class="sxs-lookup"><span data-stu-id="68bc1-109">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="68bc1-110">O acesso à funcionalidade de célula individual é fornecido pela implementação simultânea necessária do <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="68bc1-110">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="68bc1-111">Esse padrão de controle é análogo à <xref:System.Windows.Automation.Provider.IGridItemProvider> distinção que qualquer controle que implementa <xref:System.Windows.Automation.Provider.ITableItemProvider> deve expor de forma programática a relação entre a célula individual e suas informações de linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="68bc1-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="68bc1-112">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="68bc1-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="68bc1-113">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="68bc1-113">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="68bc1-114">Para obter a funcionalidade de item de grade relacionada, consulte [implementando o padrão de controle GridItem de automação da interface do usuário](implementing-the-ui-automation-griditem-control-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="68bc1-114">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="68bc1-115">Membros necessários para ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="68bc1-115">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="68bc1-116">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="68bc1-116">Required member</span></span>|<span data-ttu-id="68bc1-117">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="68bc1-117">Member type</span></span>|<span data-ttu-id="68bc1-118">Anotações</span><span class="sxs-lookup"><span data-stu-id="68bc1-118">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="68bc1-119">Método</span><span class="sxs-lookup"><span data-stu-id="68bc1-119">Method</span></span>|<span data-ttu-id="68bc1-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="68bc1-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="68bc1-121">Método</span><span class="sxs-lookup"><span data-stu-id="68bc1-121">Method</span></span>|<span data-ttu-id="68bc1-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="68bc1-122">None</span></span>|  
  
 <span data-ttu-id="68bc1-123">Este padrão de controle não tem propriedades ou eventos associados.</span><span class="sxs-lookup"><span data-stu-id="68bc1-123">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="68bc1-124">Exceções</span><span class="sxs-lookup"><span data-stu-id="68bc1-124">Exceptions</span></span>  
 <span data-ttu-id="68bc1-125">Este padrão de controle não tem nenhuma exceção associada.</span><span class="sxs-lookup"><span data-stu-id="68bc1-125">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68bc1-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="68bc1-126">See also</span></span>

- [<span data-ttu-id="68bc1-127">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="68bc1-128">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-128">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="68bc1-129">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="68bc1-129">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="68bc1-130">Implementando o padrão de controle de tabela de automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-130">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="68bc1-131">Implementando o padrão de controle GridItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-131">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="68bc1-132">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="68bc1-133">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="68bc1-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
