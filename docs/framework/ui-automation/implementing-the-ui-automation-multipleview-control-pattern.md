---
title: Implementando o padrão de controle MultipleView de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 6a77b81cab34b1824b23b1e3e050ecf034ab7700
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932166"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="6e1c1-102">Implementando o padrão de controle MultipleView de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="6e1c1-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="6e1c1-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6e1c1-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6e1c1-105">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="6e1c1-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="6e1c1-107">O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para dar suporte a controles que fornecem e são capazes de alternar entre, várias representações do mesmo conjunto de informações ou controles filho.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="6e1c1-108">Exemplos de controles que podem apresentar várias exibições incluem o modo de exibição de lista (que pode mostrar seu conteúdo como miniaturas, blocos, ícones ou [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] detalhes), gráficos (pizza, linha, barra, valor de célula com [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] uma fórmula), documentos (normal, layout da Web, layout de impressão, layout de leitura, estrutura de tópicos), calendário do Microsoft Outlook (ano, mês, semana [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] , dia) e capas.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="6e1c1-109">As exibições com suporte são determinadas pelo desenvolvedor de controle e são específicas para cada controle.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="6e1c1-110">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="6e1c1-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="6e1c1-111">Ao implementar o padrão de controle Multiple View, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="6e1c1-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="6e1c1-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>também deve ser implementado em um contêiner que gerencia a exibição atual se ele for diferente de um controle que fornece a exibição atual.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="6e1c1-113">Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo da pasta atual, enquanto a exibição do controle é gerenciada por meio do aplicativo do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="6e1c1-114">Um controle que é capaz de classificar seu conteúdo não é considerado para dar suporte a várias exibições.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="6e1c1-115">A coleção de exibições deve ser idêntica entre instâncias.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="6e1c1-116">Os nomes de exibição devem ser adequados para uso em Conversão de Texto em Fala, Braille e outros aplicativos legíveis.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="6e1c1-117">Membros necessários para IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="6e1c1-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="6e1c1-118">As propriedades e os métodos a seguir são necessários para implementar IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="6e1c1-119">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="6e1c1-119">Required members</span></span>|<span data-ttu-id="6e1c1-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="6e1c1-120">Member type</span></span>|<span data-ttu-id="6e1c1-121">Observações</span><span class="sxs-lookup"><span data-stu-id="6e1c1-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="6e1c1-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6e1c1-122">Property</span></span>|<span data-ttu-id="6e1c1-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e1c1-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="6e1c1-124">Método</span><span class="sxs-lookup"><span data-stu-id="6e1c1-124">Method</span></span>|<span data-ttu-id="6e1c1-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e1c1-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="6e1c1-126">Método</span><span class="sxs-lookup"><span data-stu-id="6e1c1-126">Method</span></span>|<span data-ttu-id="6e1c1-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e1c1-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="6e1c1-128">Método</span><span class="sxs-lookup"><span data-stu-id="6e1c1-128">Method</span></span>|<span data-ttu-id="6e1c1-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e1c1-129">None</span></span>|  
  
 <span data-ttu-id="6e1c1-130">Não há eventos associados a este padrão de controle.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="6e1c1-131">Exceções</span><span class="sxs-lookup"><span data-stu-id="6e1c1-131">Exceptions</span></span>  
 <span data-ttu-id="6e1c1-132">O provedor deve lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="6e1c1-133">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="6e1c1-133">Exception type</span></span>|<span data-ttu-id="6e1c1-134">Condição</span><span class="sxs-lookup"><span data-stu-id="6e1c1-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="6e1c1-135"><xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> Quando ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é membro da coleção views com suporte.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e1c1-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e1c1-136">See also</span></span>

- [<span data-ttu-id="6e1c1-137">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="6e1c1-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="6e1c1-138">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="6e1c1-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="6e1c1-139">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="6e1c1-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="6e1c1-140">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="6e1c1-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="6e1c1-141">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="6e1c1-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
