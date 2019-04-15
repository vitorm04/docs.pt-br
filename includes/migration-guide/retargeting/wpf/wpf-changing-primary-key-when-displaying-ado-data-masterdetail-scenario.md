---
ms.openlocfilehash: 2cd107dc92fd0fae89717c38840ce7ea44f3ac9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233899"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF alterando uma chave primária ao exibir dados ADO em um cenário de detalhes/mestre

|   |   |
|---|---|
|Detalhes|Suponha que você tenha uma coleção ADO de itens do tipo <code>Order</code>, com uma relação denominada &quot;OrderDetails&quot;, relacionando-a a uma coleção de itens do tipo <code>Detail</code> por meio da chave primária &quot;OrderID&quot;. No seu aplicativo WPF, você pode vincular um controle de lista aos detalhes de determinado pedido:<pre><code class="lang-xml">&lt;ListBox ItemsSource=&quot;{Binding Path=OrderDetails}&quot; &gt;&#13;&#10;</code></pre>em que o DataContext é um <code>Order</code>. O WPF obtém o valor da propriedade <code>OrderDetails</code> - uma coleção D de todos os itens <code>Detail</code> cuja <code>OrderID</code> corresponde à <code>OrderID</code> do item mestre. A alteração de comportamento surge quando você altera a chave primária <code>OrderID</code> do item mestre. O ADO altera automaticamente a <code>OrderID</code> de cada um dos registros afetados na coleção Detalhes (ou seja, os que foram copiados na coleção D).  Mas o que acontece com D?<ul><li>Comportamento antigo:   a coleção D é apagada.   O item mestre <em>não</em> gera uma notificação de alteração para a propriedade <code>OrderDetails</code>.  O ListBox continua a usar a coleção D, que agora está vazia.</li><li>Comportamento novo:  a coleção D permanecerá inalterada.   Cada um dos seus itens gera uma notificação de alteração para a propriedade <code>OrderID</code>.  O ListBox continua a usar a coleção D e exibe os detalhes com a nova <code>OrderID</code>.</li></ul>O WPF implementa o novo comportamento criando a coleção D de uma maneira diferente: chamando o método ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> com o argumento <code>followParent</code> definido como <code>true</code>.|
|Sugestão|Um aplicativo obtém o novo comportamento usando o comutador AppContext a seguir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;&#13;&#10;</code></pre>O padrão do comutador é <code>true</code> (comportamento antigo) para aplicativos direcionados para o .NET 4.7.1 ou anterior e <code>false</code> (novo comportamento) para aplicativos direcionados para o .NET 4.7.2 ou posterior.|
|Escopo|Secundário|
|Versão|4.7.2|
|Tipo|Redirecionando|
