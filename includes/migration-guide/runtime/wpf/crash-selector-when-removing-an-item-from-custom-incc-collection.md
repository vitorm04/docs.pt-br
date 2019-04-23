---
ms.openlocfilehash: a573a78109036b87201b53f72aa8dba6755e7a21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803132"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Seletor falha ao remover um item de uma coleção INCC personalizada

|   |   |
|---|---|
|Detalhes|Um <code>T:System.InvalidOperationException</code> pode ocorrer no seguinte cenário:<ul><li>O ItemsSource de um <code>T:System.Windows.Controls.Primitives.Selector</code> é uma coleção com uma implementação personalizada de <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>O item selecionado é removido da coleção.</li><li>O <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> tem <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1, o que indica uma posição desconhecida.</li></ul>A pilha de chamadas da exceção começa em System.Windows.Threading.Dispatcher.VerifyAccess() em System.Windows.DependencyObject.GetValue(DependencyProperty dp) em System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element). Essa exceção poderá ocorrer no .NET Framework 4.5 se o aplicativo tiver mais que um thread Dispatcher. No .NET Framework 4.7, a exceção também pode ocorrer em aplicativos com um único thread Dispatcher. O problema foi corrigido no .NET Framework 4.7.1.|
|Sugestão|Atualizar para o .NET Framework 4.7.1.|
|Escopo|Secundário|
|Versão|4.7|
|Tipo|Tempo de execução|
