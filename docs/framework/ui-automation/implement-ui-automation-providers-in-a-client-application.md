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
ms.openlocfilehash: ef3d03bee412b97ed88ec76e81ad2fd19a9595eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968953"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementar provedores de automação de interface do usuário em um aplicativo cliente
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico contém um código de exemplo que mostra como implementar um provedor de automação de interface do usuário no lado do cliente em um aplicativo.  
  
 Esse é um cenário incomum. Geralmente, um aplicativo cliente de automação de interface do usuário usa provedores do lado do servidor ou provedores do lado do cliente que residem em uma DLL.  
  
## <a name="example"></a>Exemplo  
 O código de exemplo a seguir implementa um provedor simples para uma janela de console. O código não tem nenhuma funcionalidade útil, mas destina-se a demonstrar as etapas básicas na configuração de um provedor dentro do código do cliente e seu registro usando <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>o.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral dos provedores de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Registrar um assembly do provedor do lado do cliente](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [Criar um provedor de automação de interface do usuário do lado do cliente](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementação de provedor de automação de interface do usuário do lado do cliente](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
