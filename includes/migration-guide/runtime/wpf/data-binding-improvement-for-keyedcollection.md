---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621916"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="15266-101">Melhoria de Associação de Dados para KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="15266-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="15266-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="15266-102">Details</span></span>

<span data-ttu-id="15266-103">Corrigido o <xref:System.Windows.Data.Binding> uso incorreto de um indexador de IList quando o objeto de origem declara um indexador personalizado com a mesma assinatura (por exemplo, &lt; TItem &gt; ).</span><span class="sxs-lookup"><span data-stu-id="15266-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="15266-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="15266-104">Suggestion</span></span>

<span data-ttu-id="15266-105">Para que um aplicativo destinado a uma versão mais antiga se beneficie dessa alteração, ele deve ser executado no .NET Framework 4,8 ou posterior e deve aceitar a alteração adicionando o seguinte [comutador AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) à <code>&lt;runtime&gt;</code> seção do arquivo de configuração do aplicativo e definindo-o como <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="15266-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="15266-106">Name</span><span class="sxs-lookup"><span data-stu-id="15266-106">Name</span></span>    | <span data-ttu-id="15266-107">Valor</span><span class="sxs-lookup"><span data-stu-id="15266-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="15266-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="15266-108">Scope</span></span>   |<span data-ttu-id="15266-109">Principal</span><span class="sxs-lookup"><span data-stu-id="15266-109">Major</span></span>|
|<span data-ttu-id="15266-110">Versão</span><span class="sxs-lookup"><span data-stu-id="15266-110">Version</span></span>|<span data-ttu-id="15266-111">4.8</span><span class="sxs-lookup"><span data-stu-id="15266-111">4.8</span></span>|
|<span data-ttu-id="15266-112">Type</span><span class="sxs-lookup"><span data-stu-id="15266-112">Type</span></span>|<span data-ttu-id="15266-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="15266-113">Runtime</span></span>|
