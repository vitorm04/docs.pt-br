---
title: Padrões de controle de suporte em um provedor de automação da interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: da423af259ac3ef88d5b52d576d3ab5ebb4f916e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971797"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Padrões de controle de suporte em um provedor de automação da interface do usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.

Este tópico mostra como implementar um ou mais padrões de controle em um provedor de automação de interface do usuário para que os aplicativos cliente possam manipular controles e obter dados deles.

## <a name="support-control-patterns"></a>Padrões de controle de suporte

1. Implemente as interfaces apropriadas para os padrões de controle aos quais o elemento deve dar <xref:System.Windows.Automation.Provider.IInvokeProvider> suporte <xref:System.Windows.Automation.InvokePattern>, como para.

2. Retornar o objeto que contém a implementação de cada interface de controle em sua implementação de<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma implementação <xref:System.Windows.Automation.Provider.ISelectionProvider> de para uma caixa de listagem personalizada de seleção única. Ele retorna três propriedades e Obtém o item selecionado no momento.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma implementação <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> de que retorna a classe <xref:System.Windows.Automation.Provider.ISelectionProvider>que está implementando. A maioria dos controles de caixa de listagem também ofereceria suporte a outros padrões, mas neste exemplo`Nothing` uma referência nula (no Microsoft Visual Basic .net) é retornada para todos os outros identificadores de padrão.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Consulte também

- [Visão geral dos provedores de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
