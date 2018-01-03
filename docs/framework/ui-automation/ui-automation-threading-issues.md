---
title: "Problemas de Threading na Automação da Interface do Usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
caps.latest.revision: "9"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9e5c38f5c4681210a4f3be552a3f08be3962bc2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-threading-issues"></a><span data-ttu-id="7c5a2-102">Problemas de Threading na Automação da Interface do Usuário</span><span class="sxs-lookup"><span data-stu-id="7c5a2-102">UI Automation Threading Issues</span></span>
> [!NOTE]
>  <span data-ttu-id="7c5a2-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7c5a2-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="7c5a2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7c5a2-105">Por causa da forma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] usa mensagens do Windows, conflitos pode ocorrer quando um aplicativo cliente tenta interagir com seu próprio [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-105">Because of the way [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uses Windows messages, conflicts can occur when a client application attempts to interact with its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] on the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="7c5a2-106">Esses conflitos podem resultar em um desempenho muito lento ou até mesmo fazer com que o aplicativo pare de responder.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-106">These conflicts can lead to very slow performance or even cause the application to stop responding.</span></span>  
  
 <span data-ttu-id="7c5a2-107">Se seu aplicativo cliente se destina a interagir com todos os elementos na área de trabalho, incluindo sua própria [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer todas as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chama em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-107">If your client application is intended to interact with all elements on the desktop, including its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you should make all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls on a separate thread.</span></span> <span data-ttu-id="7c5a2-108">Isso inclui localizar elementos (por exemplo, usando <xref:System.Windows.Automation.TreeWalker> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A> método) e usando os padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-108">This includes locating elements (for example, by using <xref:System.Windows.Automation.TreeWalker> or the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method) and using control patterns.</span></span>  
  
 <span data-ttu-id="7c5a2-109">É seguro fazer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chamadas dentro de um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] manipulador de eventos, porque o manipulador de eventos é sempre chamado em uma não -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-109">It is safe to make [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event handler, because the event handler is always called on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="7c5a2-110">No entanto, ao assinar eventos que podem se originar de seu aplicativo de cliente [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer a chamada para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ou um método relacionado, em não[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-110">However, when subscribing to events that may originate from your client application's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you must make the call to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, or a related method, on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="7c5a2-111">Remova manipuladores de eventos no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="7c5a2-111">Remove event handlers on the same thread.</span></span>
