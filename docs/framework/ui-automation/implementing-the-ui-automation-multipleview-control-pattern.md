---
title: Implementando o padrão de controle MultipleView de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 699644b98fbf818c71553775f4dff8dfb0726977
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043436"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="15398-102">Implementando o padrão de controle MultipleView de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="15398-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="15398-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="15398-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="15398-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="15398-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="15398-105">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="15398-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="15398-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="15398-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="15398-107">O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para dar suporte a controles que fornecem e são capazes de alternar entre, várias representações do mesmo conjunto de informações ou controles filho.</span><span class="sxs-lookup"><span data-stu-id="15398-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="15398-108">Exemplos de controles que podem apresentar várias exibições incluem o modo de exibição de lista (que pode mostrar seu conteúdo como miniaturas, blocos, ícones ou [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] detalhes), gráficos (pizza, linha, barra, valor de célula com [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] uma fórmula), documentos (normal, layout da Web, layout de impressão, layout de leitura, estrutura de tópicos), calendário do Microsoft Outlook (ano, mês, semana [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] , dia) e capas.</span><span class="sxs-lookup"><span data-stu-id="15398-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="15398-109">As exibições com suporte são determinadas pelo desenvolvedor de controle e são específicas para cada controle.</span><span class="sxs-lookup"><span data-stu-id="15398-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="15398-110">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="15398-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="15398-111">Ao implementar o padrão de controle Multiple View, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="15398-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="15398-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>também deve ser implementado em um contêiner que gerencia a exibição atual se ele for diferente de um controle que fornece a exibição atual.</span><span class="sxs-lookup"><span data-stu-id="15398-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="15398-113">Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo da pasta atual, enquanto a exibição do controle é gerenciada por meio do aplicativo do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="15398-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="15398-114">Um controle que é capaz de classificar seu conteúdo não é considerado para dar suporte a várias exibições.</span><span class="sxs-lookup"><span data-stu-id="15398-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="15398-115">A coleção de exibições deve ser idêntica entre instâncias.</span><span class="sxs-lookup"><span data-stu-id="15398-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="15398-116">Os nomes de exibição devem ser adequados para uso em Conversão de Texto em Fala, Braille e outros aplicativos legíveis.</span><span class="sxs-lookup"><span data-stu-id="15398-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="15398-117">Membros necessários para IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="15398-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="15398-118">As propriedades e os métodos a seguir são necessários para implementar IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="15398-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="15398-119">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="15398-119">Required members</span></span>|<span data-ttu-id="15398-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="15398-120">Member type</span></span>|<span data-ttu-id="15398-121">Observações</span><span class="sxs-lookup"><span data-stu-id="15398-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="15398-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="15398-122">Property</span></span>|<span data-ttu-id="15398-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="15398-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="15398-124">Método</span><span class="sxs-lookup"><span data-stu-id="15398-124">Method</span></span>|<span data-ttu-id="15398-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="15398-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="15398-126">Método</span><span class="sxs-lookup"><span data-stu-id="15398-126">Method</span></span>|<span data-ttu-id="15398-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="15398-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="15398-128">Método</span><span class="sxs-lookup"><span data-stu-id="15398-128">Method</span></span>|<span data-ttu-id="15398-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="15398-129">None</span></span>|  
  
 <span data-ttu-id="15398-130">Não há eventos associados a este padrão de controle.</span><span class="sxs-lookup"><span data-stu-id="15398-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="15398-131">Exceções</span><span class="sxs-lookup"><span data-stu-id="15398-131">Exceptions</span></span>  
 <span data-ttu-id="15398-132">O provedor deve lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="15398-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="15398-133">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="15398-133">Exception type</span></span>|<span data-ttu-id="15398-134">Condição</span><span class="sxs-lookup"><span data-stu-id="15398-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="15398-135"><xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> Quando ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é membro da coleção views com suporte.</span><span class="sxs-lookup"><span data-stu-id="15398-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15398-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15398-136">See also</span></span>

- [<span data-ttu-id="15398-137">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="15398-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="15398-138">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="15398-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="15398-139">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="15398-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="15398-140">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="15398-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="15398-141">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="15398-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
