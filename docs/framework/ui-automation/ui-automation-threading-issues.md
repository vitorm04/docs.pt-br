---
title: Problemas de Threading na Automação da Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 8dc21a680a19933e9db8d52a0e6b7e6ffdd333f8
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800829"
---
# <a name="ui-automation-threading-issues"></a>Problemas de Threading na Automação da Interface do Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Devido à maneira como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] usa mensagens do Windows, os conflitos podem ocorrer quando um aplicativo cliente tenta interagir com seus próprios [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] no thread [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Esses conflitos podem levar a um desempenho muito lento ou até mesmo fazer com que o aplicativo pare de responder.  
  
 Se o seu aplicativo cliente se destina a interagir com todos os elementos na área de trabalho, incluindo seu próprio [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], você deve fazer todas as chamadas de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em um thread separado. Isso inclui a localização de elementos (por exemplo, usando <xref:System.Windows.Automation.TreeWalker> ou o método <xref:System.Windows.Automation.AutomationElement.FindAll%2A>) e o uso de padrões de controle.  
  
 É seguro fazer chamadas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em um manipulador de eventos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], porque o manipulador de eventos é sempre chamado em um thread não[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. No entanto, ao assinar eventos que podem se originar do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]do seu aplicativo cliente, você deve fazer a chamada para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>ou um método relacionado em um thread não[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Remova os manipuladores de eventos no mesmo thread.
