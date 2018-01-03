---
title: "Implementando o Padrão Controle de Window de Automação de Interface de Usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3f1b44184f1a241943d9fa9d60a62a703dbaf0d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="f828a-102">Implementando o Padrão Controle de Window de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="f828a-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="f828a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f828a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f828a-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="f828a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f828a-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IWindowProvider>, incluindo informações sobre <xref:System.Windows.Automation.WindowPattern> propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="f828a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="f828a-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="f828a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="f828a-107">O <xref:System.Windows.Automation.WindowPattern> padrão de controle é usado para oferecer suporte aos controles que fornecem funcionalidade fundamental de janela dentro de um tradicional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f828a-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="f828a-108">Exemplos de controles que devem implementar esse padrão de controle de nível superior do aplicativo windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] janelas filho, controles de painel dividido redimensionáveis, caixas de diálogo modais e balão de ajudam windows.</span><span class="sxs-lookup"><span data-stu-id="f828a-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="f828a-109">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="f828a-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="f828a-110">Ao implementar o padrão de controle de janela, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="f828a-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="f828a-111">Para dar suporte a capacidade de modificar tanto o tamanho da janela e posição na tela usando automação de interface do usuário, um controle deve implementar <xref:System.Windows.Automation.Provider.ITransformProvider> além <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="f828a-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="f828a-112">Controles que contêm barras de título e elementos de barra de título que permitem o controle a ser movido, redimensionado, maximizado, minimizado, ou fechado são geralmente necessários para implementar <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="f828a-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="f828a-113">Controles como dica de ferramenta pop-ups e combinação caixa ou menus suspensos normalmente não implementam <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="f828a-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="f828a-114">Janelas da Ajuda de balão são diferenciadas de pop-ups de dica de ferramenta básica por do fornecimento de um botão Fechar como de janela.</span><span class="sxs-lookup"><span data-stu-id="f828a-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="f828a-115">Modo de tela inteira não é suportado por IWindowProvider pois ele é um recurso específico para um aplicativo e não é o comportamento de janela típica.</span><span class="sxs-lookup"><span data-stu-id="f828a-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="f828a-116">Membros necessários para IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="f828a-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="f828a-117">As seguintes propriedades, métodos e eventos são necessários para a interface IWindowProvider.</span><span class="sxs-lookup"><span data-stu-id="f828a-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="f828a-118">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="f828a-118">Required member</span></span>|<span data-ttu-id="f828a-119">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="f828a-119">Member type</span></span>|<span data-ttu-id="f828a-120">Observações</span><span class="sxs-lookup"><span data-stu-id="f828a-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="f828a-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f828a-121">Property</span></span>|<span data-ttu-id="f828a-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="f828a-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f828a-123">Property</span></span>|<span data-ttu-id="f828a-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="f828a-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f828a-125">Property</span></span>|<span data-ttu-id="f828a-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="f828a-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f828a-127">Property</span></span>|<span data-ttu-id="f828a-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="f828a-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f828a-129">Property</span></span>|<span data-ttu-id="f828a-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="f828a-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f828a-131">Property</span></span>|<span data-ttu-id="f828a-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="f828a-133">Método</span><span class="sxs-lookup"><span data-stu-id="f828a-133">Method</span></span>|<span data-ttu-id="f828a-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="f828a-135">Método</span><span class="sxs-lookup"><span data-stu-id="f828a-135">Method</span></span>|<span data-ttu-id="f828a-136">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="f828a-137">Método</span><span class="sxs-lookup"><span data-stu-id="f828a-137">Method</span></span>|<span data-ttu-id="f828a-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="f828a-139">evento</span><span class="sxs-lookup"><span data-stu-id="f828a-139">Event</span></span>|<span data-ttu-id="f828a-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="f828a-141">evento</span><span class="sxs-lookup"><span data-stu-id="f828a-141">Event</span></span>|<span data-ttu-id="f828a-142">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f828a-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="f828a-143">evento</span><span class="sxs-lookup"><span data-stu-id="f828a-143">Event</span></span>|<span data-ttu-id="f828a-144">Não é garantido para ser<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="f828a-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="f828a-145">Exceções</span><span class="sxs-lookup"><span data-stu-id="f828a-145">Exceptions</span></span>  
 <span data-ttu-id="f828a-146">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="f828a-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="f828a-147">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="f828a-147">Exception type</span></span>|<span data-ttu-id="f828a-148">Condição</span><span class="sxs-lookup"><span data-stu-id="f828a-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="f828a-149">-Quando um controle não oferece suporte a um comportamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="f828a-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="f828a-150">-Quando o parâmetro não é um número válido.</span><span class="sxs-lookup"><span data-stu-id="f828a-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f828a-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f828a-151">See Also</span></span>  
 [<span data-ttu-id="f828a-152">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f828a-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="f828a-153">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f828a-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="f828a-154">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="f828a-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="f828a-155">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f828a-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="f828a-156">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f828a-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
