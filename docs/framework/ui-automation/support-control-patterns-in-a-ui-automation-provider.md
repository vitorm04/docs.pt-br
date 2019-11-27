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
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446824"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Padrões de controle de suporte em um provedor de automação da interface do usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).

Este tópico mostra como implementar um ou mais padrões de controle em um provedor de automação de interface do usuário para que os aplicativos cliente possam manipular controles e obter dados deles.

## <a name="support-control-patterns"></a>Padrões de controle de suporte

1. Implemente as interfaces apropriadas para os padrões de controle aos quais o elemento deve dar suporte, como <xref:System.Windows.Automation.Provider.IInvokeProvider> para <xref:System.Windows.Automation.InvokePattern>.

2. Retorne o objeto que contém a implementação de cada interface de controle em sua implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma implementação de <xref:System.Windows.Automation.Provider.ISelectionProvider> para uma caixa de listagem personalizada de seleção única. Ele retorna três propriedades e Obtém o item selecionado no momento.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> que retorna a classe que está implementando <xref:System.Windows.Automation.Provider.ISelectionProvider>. A maioria dos controles de caixa de listagem também ofereceria suporte a outros padrões, mas neste exemplo uma referência nula (`Nothing` no Microsoft Visual Basic .NET) é retornada para todos os outros identificadores de padrão.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Consulte também

- [Visão geral dos provedores de automação de interface do usuário](ui-automation-providers-overview.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](server-side-ui-automation-provider-implementation.md)
