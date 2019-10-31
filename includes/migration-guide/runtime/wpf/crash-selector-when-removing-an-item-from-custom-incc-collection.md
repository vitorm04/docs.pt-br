---
ms.openlocfilehash: 8f4ee44e8432bae3537c6f064f564b9f044a7c33
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802540"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Seletor falha ao remover um item de uma coleção INCC personalizada

|   |   |
|---|---|
|Detalhes|Um <code>T:System.InvalidOperationException</code> pode ocorrer no seguinte cenário:<ul><li>O ItemsSource de um <code>T:System.Windows.Controls.Primitives.Selector</code> é uma coleção com uma implementação personalizada de <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>O item selecionado é removido da coleção.</li><li>O <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> tem <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1, o que indica uma posição desconhecida.</li></ul>A pilha de chamadas da exceção começa em System.Windows.Threading.Dispatcher.VerifyAccess() em System.Windows.DependencyObject.GetValue(DependencyProperty dp) em System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element). Essa exceção poderá ocorrer no .NET Framework 4.5 se o aplicativo tiver mais que um thread Dispatcher. No .NET Framework 4.7, a exceção também pode ocorrer em aplicativos com um único thread Dispatcher. O problema foi corrigido no .NET Framework 4.7.1.|
|Sugestão|Atualizar para o .NET Framework 4.7.1.|
|Escopo|Secundário|
|Versão|4.7|
|Tipo|Tempo de execução|

