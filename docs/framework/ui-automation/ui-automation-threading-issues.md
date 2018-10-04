---
title: Problemas de Threading na Automação da Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7d8df325d18c3657d4955fa534d29bb7fdbc595c
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48265929"
---
# <a name="ui-automation-threading-issues"></a>Problemas de Threading na Automação da Interface do Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Devido à maneira [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] usa mensagens do Windows, conflitos pode ocorrer quando um aplicativo cliente tenta interagir com seu próprio [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sobre o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread. Esses conflitos podem levar a um desempenho muito lento ou até mesmo fazer com que o aplicativo pare de responder.  
  
 Se seu aplicativo cliente se destina a interagir com todos os elementos na área de trabalho, incluindo sua própria [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer todas as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chama em um thread separado. Isso inclui localizar elementos (por exemplo, usando <xref:System.Windows.Automation.TreeWalker> ou o <xref:System.Windows.Automation.AutomationElement.FindAll%2A> método) e usando padrões de controle.  
  
 É seguro fazer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chama dentro de uma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] manipulador de eventos, porque o manipulador de eventos é sempre chamado em um não -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread. No entanto, ao assinar eventos que podem ser obtidas de seu aplicativo de cliente [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer a chamada para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ou um método relacionado, em um não -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread. Remova manipuladores de eventos no mesmo thread.
