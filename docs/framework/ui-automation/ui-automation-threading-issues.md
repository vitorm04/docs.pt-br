---
title: Problemas de Threading na Automação da Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: f4820d2db6275e3c1ae9b55754b8cb6fec6fcc56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954055"
---
# <a name="ui-automation-threading-issues"></a>Problemas de Threading na Automação da Interface do Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Devido à maneira [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] como o usa mensagens do Windows, os conflitos podem ocorrer quando um aplicativo cliente tenta interagir com [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] seu próprio no thread. Esses conflitos podem levar a um desempenho muito lento ou até mesmo fazer com que o aplicativo pare de responder.  
  
 Se o seu aplicativo cliente se destina a interagir com todos os elementos na área de trabalho, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]incluindo seu próprio, você [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] deve fazer todas as chamadas em um thread separado. Isso inclui a localização de elementos (por exemplo, <xref:System.Windows.Automation.TreeWalker> usando o <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ou o método) e o uso de padrões de controle.  
  
 É seguro fazer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chamadas dentro de um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] manipulador de eventos, pois o manipulador de eventos é sempre[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] chamado em um não thread. No entanto, ao assinar eventos que podem se originar de seus aplicativos [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]cliente, você deve fazer a chamada para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ou um método relacionado[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , em um não thread. Remova os manipuladores de eventos no mesmo thread.
