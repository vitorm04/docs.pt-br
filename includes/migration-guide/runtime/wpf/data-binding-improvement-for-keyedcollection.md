---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802693"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Melhoria de Associação de Dados para KeyedCollection

|   |   |
|---|---|
|Detalhes|Correção do uso incorreto de <xref:System.Windows.Data.Binding> do indexador IList quando o objeto de origem declara um indexador personalizado com a mesma assinatura (por ex., KeyedCollection&lt;int,TItem&gt;).|
|Sugestão|Para que o aplicativo se beneficie dessa alteração, ele deve ser executado no .NET Framework 4.7.2 ou posterior e deve aceitar a alteração adicionando o seguinte [comutador AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração do aplicativo e definindo-o como <code>false</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Principal|
|Versão|4.8|
|Tipo|Tempo de execução|

