---
title: Retornando Propriedades de um Provedor de Automação de IU
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 905e689ce0936bdc24fc2d75c2022ea698e682a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526373"
---
# <a name="return-properties-from-a-ui-automation-provider"></a>Retornando Propriedades de um Provedor de Automação de IU
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico contém código de exemplo que mostra como um provedor de automação de interface do usuário pode retornar propriedades de um elemento para aplicativos cliente.  
  
 Para qualquer propriedade que não oferece suporte explicitamente, o provedor deve retornar `null` (`Nothing` no Visual Basic). Isso garante que [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tenta obter a propriedade de outra fonte, como o provedor de janela de host.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral dos provedores de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
