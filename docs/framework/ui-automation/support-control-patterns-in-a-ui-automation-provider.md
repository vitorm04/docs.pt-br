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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0c7ca4507ce5e7d2f6f295caace23134a8a6d492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Padrões de controle de suporte em um provedor de automação da interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como implementar um ou mais padrões de controle em um provedor de automação de interface do usuário para que os aplicativos cliente possam manipular os controles e obter dados deles.  
  
### <a name="support-control-patterns"></a>Suporte a padrões de controle  
  
1.  Implemente as interfaces apropriadas para os padrões de controle que o elemento deve suportar, como <xref:System.Windows.Automation.Provider.IInvokeProvider> para <xref:System.Windows.Automation.InvokePattern>.  
  
2.  Retornar o objeto que contém a implementação de cada interface de controle na sua implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação de <xref:System.Windows.Automation.Provider.ISelectionProvider> para uma caixa de listagem de seleção única personalizado. Ela retorna três propriedades e obtém o item atualmente selecionado.  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> que retorna a classe que implementa <xref:System.Windows.Automation.Provider.ISelectionProvider>. A maioria dos controles de caixa de lista suportaria outros padrões também, mas nesse exemplo uma referência nula (`Nothing` no Microsoft Visual Basic .NET) é retornado para todos os outros identificadores de padrão.  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral dos provedores de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
