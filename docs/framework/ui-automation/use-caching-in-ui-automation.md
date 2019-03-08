---
title: Usar armazenamento em cache em automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 0c12b8347e0dfe239189a7e1d1569aaf2dabc0a2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675492"
---
# <a name="use-caching-in-ui-automation"></a>Usar armazenamento em cache em automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Esta seção mostra como implementar o cache de <xref:System.Windows.Automation.AutomationElement> propriedades e padrões de controle.  
  
### <a name="activate-a-cache-request"></a>Ativar uma solicitação de Cache  
  
1.  Criará um <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Especifique as propriedades e padrões para cache usando <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3.  Especifique o escopo de armazenamento em cache, definindo o <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> propriedade.  
  
4.  Especifique o modo de exibição da subárvore, definindo o <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> propriedade.  
  
5.  Defina as <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> propriedade para <xref:System.Windows.Automation.AutomationElementMode.None> se você quiser aumentar a eficiência não recuperando uma referência completa a objetos. (Isso tornará impossível recuperar valores atuais desses objetos.)  
  
6.  Ativar a solicitação usando <xref:System.Windows.Automation.CacheRequest.Activate%2A> dentro de um `using` bloco (`Using` no Microsoft Visual Basic .NET).  
  
 Depois de obter <xref:System.Windows.Automation.AutomationElement> objetos ou inscrever-se em eventos, desative a solicitação usando <xref:System.Windows.Automation.CacheRequest.Pop%2A> (se <xref:System.Windows.Automation.CacheRequest.Push%2A> foi usado) ou removendo o objeto criado pelo <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> em um `using` bloco (`Using` no Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Propriedades do cache AutomationElement  
  
1.  Enquanto um <xref:System.Windows.Automation.CacheRequest> está ativa, obter <xref:System.Windows.Automation.AutomationElement> objetos usando <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; ou obtenha um <xref:System.Windows.Automation.AutomationElement> como a origem de um evento que você registrou para quando o <xref:System.Windows.Automation.CacheRequest> estava ativo. (Você também pode criar um cache, passando um <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache ou um do <xref:System.Windows.Automation.TreeWalker> métodos.)  
  
2.  Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou recuperar uma propriedade do <xref:System.Windows.Automation.AutomationElement.Cached%2A> propriedade do <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Obter padrões em cache e suas propriedades  
  
1.  Enquanto um <xref:System.Windows.Automation.CacheRequest> está ativa, obter <xref:System.Windows.Automation.AutomationElement> objetos usando <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; ou obtenha um <xref:System.Windows.Automation.AutomationElement> como a origem de um evento que você registrou para quando o <xref:System.Windows.Automation.CacheRequest> estava ativo. (Você também pode criar um cache, passando um <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache ou um do <xref:System.Windows.Automation.TreeWalker> métodos.)  
  
2.  Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> para recuperar um padrão armazenado em cache.  
  
3.  Recuperar valores de propriedade a `Cached` propriedade do padrão de controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra vários aspectos do armazenamento em cache, usando <xref:System.Windows.Automation.CacheRequest.Activate%2A> para ativar o <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra vários aspectos do armazenamento em cache, usando <xref:System.Windows.Automation.CacheRequest.Push%2A> para ativar o <xref:System.Windows.Automation.CacheRequest>. Exceto quando você quiser aninhar solicitações de cache, é preferível usar <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Consulte também
- [Armazenamento em cache em clientes de automação de interface do usuário](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
