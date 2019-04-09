---
title: Implementar provedores de automação de interface do usuário em um aplicativo cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: b368ab3bc842fda5a99a64e0220093ebd60698b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105918"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementar provedores de automação de interface do usuário em um aplicativo cliente
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico contém código de exemplo que mostra como implementar um provedor de automação de interface do usuário do lado do cliente dentro de um aplicativo.  
  
 Isso é um cenário incomum. Geralmente, um aplicativo de cliente de automação de interface do usuário usa provedores do lado do servidor, ou provedores do lado do cliente que residem em uma DLL.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir implementa um provedor simples para uma janela do console. O código não tem nenhuma funcionalidade útil, mas serve para demonstrar as etapas básicas na configuração de um provedor de código do cliente e registrando-a usando <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Consulte também

- [Visão Geral dos Provedores de Automação de Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Registrar um Módulo Provedor do Lado do Cliente](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [Criar um Provedor de Automação de Interface de Usuário do Lado do Cliente](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementação de Provedor de Automação de Interface de Usuário do Lado do Cliente](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
