---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802693"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="2587c-101">Melhoria de Associação de Dados para KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="2587c-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2587c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2587c-102">Details</span></span>|<span data-ttu-id="2587c-103">Correção do uso incorreto de <xref:System.Windows.Data.Binding> do indexador IList quando o objeto de origem declara um indexador personalizado com a mesma assinatura (por ex., KeyedCollection&lt;int,TItem&gt;).</span><span class="sxs-lookup"><span data-stu-id="2587c-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (e.g. KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="2587c-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2587c-104">Suggestion</span></span>|<span data-ttu-id="2587c-105">Para que o aplicativo se beneficie dessa alteração, ele deve ser executado no .NET Framework 4.7.2 ou posterior e deve aceitar a alteração adicionando o seguinte [comutador AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração do aplicativo e definindo-o como <code>false</code>:</span><span class="sxs-lookup"><span data-stu-id="2587c-105">In order for the application to benefit from this change, it must run on the .NET Framework 4.7.2 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="2587c-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="2587c-106">Scope</span></span>|<span data-ttu-id="2587c-107">Principal</span><span class="sxs-lookup"><span data-stu-id="2587c-107">Major</span></span>|
|<span data-ttu-id="2587c-108">Versão</span><span class="sxs-lookup"><span data-stu-id="2587c-108">Version</span></span>|<span data-ttu-id="2587c-109">4.8</span><span class="sxs-lookup"><span data-stu-id="2587c-109">4.8</span></span>|
|<span data-ttu-id="2587c-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="2587c-110">Type</span></span>|<span data-ttu-id="2587c-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2587c-111">Runtime</span></span>|

