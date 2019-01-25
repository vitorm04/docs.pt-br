---
title: Disparar Eventos de um Provedor de Automação UI
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 328adccc2224d27230a06e8d98a691d12c5be218
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539045"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>Disparar Eventos de um Provedor de Automação UI
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico contém código de exemplo que mostra como disparar um evento de um provedor de automação de interface do usuário.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é gerado na implementação de um controle de botão personalizado. A implementação permite que um aplicativo de cliente de automação de interface do usuário simular um clique de botão.  
  
 Para evitar o processamento desnecessário, o exemplo verifica <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> para ver se os eventos devem ser disparados.  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral dos provedores de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
