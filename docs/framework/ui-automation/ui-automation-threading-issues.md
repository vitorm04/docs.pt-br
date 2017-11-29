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
ms.openlocfilehash: a1eaed2a7876c6e6981e7cc4172442b19800586b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-threading-issues"></a>Problemas de Threading na Automação da Interface do Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Por causa da forma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] usa mensagens do Windows, conflitos pode ocorrer quando um aplicativo cliente tenta interagir com seu próprio [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread. Esses conflitos podem resultar em um desempenho muito lento ou até mesmo fazer com que o aplicativo pare de responder.  
  
 Se seu aplicativo cliente se destina a interagir com todos os elementos na área de trabalho, incluindo sua própria [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer todas as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chama em um thread separado. Isso inclui localizar elementos (por exemplo, usando <xref:System.Windows.Automation.TreeWalker> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A> método) e usando os padrões de controle.  
  
 É seguro fazer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chamadas dentro de um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] manipulador de eventos, porque o manipulador de eventos é sempre chamado em uma não -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread. No entanto, ao assinar eventos que podem se originar de seu aplicativo de cliente [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer a chamada para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ou um método relacionado, em não[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread. Remova manipuladores de eventos no mesmo thread.
