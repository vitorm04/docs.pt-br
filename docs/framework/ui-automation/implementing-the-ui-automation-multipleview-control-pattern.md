---
title: 'Implementando o padrão de controle MultipleView de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180164"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="a835c-102">Implementando o padrão de controle MultipleView de interface de usuário </span><span class="sxs-lookup"><span data-stu-id="a835c-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="a835c-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a835c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a835c-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="a835c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a835c-105">Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IMultipleViewProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="a835c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="a835c-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="a835c-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a835c-107">O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para suportar controles que fornecem, e são capazes de alternar entre múltiplas representações do mesmo conjunto de informações ou controles de crianças.</span><span class="sxs-lookup"><span data-stu-id="a835c-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="a835c-108">Exemplos de controles que podem apresentar várias visualizações incluem a exibição da lista (que pode mostrar seu conteúdo como miniaturas, telhas, ícones ou detalhes), gráficos do Microsoft Excel (torta, linha, barra, valor de celular com uma fórmula), documentos do Microsoft Word (normal, layout da Web, impressão layout, layout de leitura, contorno), calendário do Microsoft Outlook (ano, mês, semana, dia) e skins do Microsoft Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="a835c-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="a835c-109">As visualizações suportadas são determinadas pelo desenvolvedor de controle e são específicas para cada controle.</span><span class="sxs-lookup"><span data-stu-id="a835c-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a835c-110">Diretrizes e Convenções de Implementação</span><span class="sxs-lookup"><span data-stu-id="a835c-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a835c-111">Ao implementar o padrão de controle de exibição múltipla, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="a835c-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="a835c-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>também deve ser implementado em um contêiner que gerencia a visualização atual se for diferente de um controle que fornece a visão atual.</span><span class="sxs-lookup"><span data-stu-id="a835c-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="a835c-113">Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo atual da pasta, enquanto a exibição do controle é gerenciada a partir do aplicativo Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="a835c-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="a835c-114">Um controle capaz de classificar seu conteúdo não é considerado para suportar múltiplas visualizações.</span><span class="sxs-lookup"><span data-stu-id="a835c-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="a835c-115">A coleção de visualizações deve ser idêntica entre as instâncias.</span><span class="sxs-lookup"><span data-stu-id="a835c-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="a835c-116">Os nomes de exibição devem ser adequados para uso em Texto para Fala, Braille e outras aplicações legíveis por humanos.</span><span class="sxs-lookup"><span data-stu-id="a835c-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="a835c-117">Membros necessários para IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="a835c-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="a835c-118">As seguintes propriedades e métodos são necessários para implementar o IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="a835c-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="a835c-119">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="a835c-119">Required members</span></span>|<span data-ttu-id="a835c-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="a835c-120">Member type</span></span>|<span data-ttu-id="a835c-121">Observações</span><span class="sxs-lookup"><span data-stu-id="a835c-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="a835c-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a835c-122">Property</span></span>|<span data-ttu-id="a835c-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a835c-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="a835c-124">Método</span><span class="sxs-lookup"><span data-stu-id="a835c-124">Method</span></span>|<span data-ttu-id="a835c-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a835c-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="a835c-126">Método</span><span class="sxs-lookup"><span data-stu-id="a835c-126">Method</span></span>|<span data-ttu-id="a835c-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a835c-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="a835c-128">Método</span><span class="sxs-lookup"><span data-stu-id="a835c-128">Method</span></span>|<span data-ttu-id="a835c-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a835c-129">None</span></span>|  
  
 <span data-ttu-id="a835c-130">Não há eventos associados a este padrão de controle.</span><span class="sxs-lookup"><span data-stu-id="a835c-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="a835c-131">Exceções</span><span class="sxs-lookup"><span data-stu-id="a835c-131">Exceptions</span></span>  
 <span data-ttu-id="a835c-132">O provedor deve lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="a835c-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="a835c-133">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="a835c-133">Exception type</span></span>|<span data-ttu-id="a835c-134">Condição</span><span class="sxs-lookup"><span data-stu-id="a835c-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="a835c-135">Quando <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é um membro da coleção de visualizações suportadas.</span><span class="sxs-lookup"><span data-stu-id="a835c-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a835c-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="a835c-136">See also</span></span>

- [<span data-ttu-id="a835c-137">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="a835c-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a835c-138">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a835c-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="a835c-139">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="a835c-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="a835c-140">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a835c-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="a835c-141">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a835c-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
