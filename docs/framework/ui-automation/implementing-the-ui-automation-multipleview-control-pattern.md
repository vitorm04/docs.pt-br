---
title: 'Implementando o padrão de controle MultipleView de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 292a1c0a57c992e847dd72a24508482cb6783121
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555741"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="5939a-102">Implementando o padrão de controle MultipleView de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="5939a-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5939a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5939a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5939a-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="5939a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5939a-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, incluindo informações sobre propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="5939a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="5939a-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="5939a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5939a-107">O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para oferecer suporte aos controles que fornecem e podem alternar entre várias representações do mesmo conjunto de informações ou controles filho.</span><span class="sxs-lookup"><span data-stu-id="5939a-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="5939a-108">Exemplos de controles que podem apresentar vários modos de exibição incluem a exibição de lista (que pode mostrar seu conteúdo como miniaturas, blocos, ícones ou obter detalhes), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] gráficos (pizza, linha, barra, valor da célula com uma fórmula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documentos (normal, layout da Web, Imprimir layout, o layout de leitura, a estrutura de tópicos), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendário (ano, mês, semana, dia), e [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] capas.</span><span class="sxs-lookup"><span data-stu-id="5939a-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="5939a-109">Os modos de exibição com suporte são determinados pelo desenvolvedor do controle e são específicos para cada controle.</span><span class="sxs-lookup"><span data-stu-id="5939a-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5939a-110">As convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="5939a-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5939a-111">Ao implementar o padrão de controle de exibição de várias, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="5939a-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="5939a-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> também deve ser implementada em um contêiner que gerencia a exibição atual se ele for diferente de um controle que fornece a exibição atual.</span><span class="sxs-lookup"><span data-stu-id="5939a-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="5939a-113">Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo da pasta atual, enquanto o modo de exibição para o controle é gerenciado do aplicativo Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="5939a-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="5939a-114">Um controle que é capaz de classificar seu conteúdo não é considerado para dar suporte a vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="5939a-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="5939a-115">A coleção de exibições deve ser idêntica entre instâncias.</span><span class="sxs-lookup"><span data-stu-id="5939a-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="5939a-116">Nomes de exibição devem ser adequados para uso em texto em fala, Braille e outros aplicativos legível por humanos.</span><span class="sxs-lookup"><span data-stu-id="5939a-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="5939a-117">Membros necessários para IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="5939a-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="5939a-118">As propriedades e métodos a seguir são necessários para implementar IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="5939a-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="5939a-119">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="5939a-119">Required members</span></span>|<span data-ttu-id="5939a-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="5939a-120">Member type</span></span>|<span data-ttu-id="5939a-121">Observações</span><span class="sxs-lookup"><span data-stu-id="5939a-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="5939a-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5939a-122">Property</span></span>|<span data-ttu-id="5939a-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5939a-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="5939a-124">Método</span><span class="sxs-lookup"><span data-stu-id="5939a-124">Method</span></span>|<span data-ttu-id="5939a-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5939a-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="5939a-126">Método</span><span class="sxs-lookup"><span data-stu-id="5939a-126">Method</span></span>|<span data-ttu-id="5939a-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5939a-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="5939a-128">Método</span><span class="sxs-lookup"><span data-stu-id="5939a-128">Method</span></span>|<span data-ttu-id="5939a-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5939a-129">None</span></span>|  
  
 <span data-ttu-id="5939a-130">Não há nenhum evento associado com esse padrão de controle.</span><span class="sxs-lookup"><span data-stu-id="5939a-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5939a-131">Exceções</span><span class="sxs-lookup"><span data-stu-id="5939a-131">Exceptions</span></span>  
 <span data-ttu-id="5939a-132">O provedor deve lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="5939a-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5939a-133">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="5939a-133">Exception type</span></span>|<span data-ttu-id="5939a-134">Condição</span><span class="sxs-lookup"><span data-stu-id="5939a-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="5939a-135">Quando o <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é um membro da coleção de exibições com suporte.</span><span class="sxs-lookup"><span data-stu-id="5939a-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5939a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5939a-136">See Also</span></span>  
 [<span data-ttu-id="5939a-137">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5939a-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="5939a-138">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5939a-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="5939a-139">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="5939a-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="5939a-140">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5939a-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="5939a-141">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5939a-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
