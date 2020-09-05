---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497586"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a><span data-ttu-id="aa5e1-101">A configuração de aplicativo "dataAnnotations:dataTypeAttribute:disableRegEx" é habilitada por padrão no .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="aa5e1-101">"dataAnnotations:dataTypeAttribute:disableRegEx" app setting is on by default in .NET Framework 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="aa5e1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="aa5e1-102">Details</span></span>

<span data-ttu-id="aa5e1-103">No .NET Framework 4.6.1, foi introduzida uma configuração de aplicativo (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) que permite que os usuários desabilitem o uso de expressões regulares em atributos de tipo de dados (como <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> e <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="aa5e1-103">In .NET Framework 4.6.1, an app setting (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) was introduced that allows users to disable the use of regular expressions in data type attributes (such as <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, and <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="aa5e1-104">Isso ajuda a reduzir vulnerabilidades de segurança, por exemplo, impedindo que um ataque de negação de serviço use expressões regulares específicas.</span><span class="sxs-lookup"><span data-stu-id="aa5e1-104">This helps to reduce security vulnerability such as avoiding the possibility of a Denial of Service attack using specific regular expressions.</span></span><br/><span data-ttu-id="aa5e1-105">No .NET Framework 4.6.1, essa configuração de aplicativo para desabilitar o uso de expressões regulares era definida como <code>false</code> por padrão.</span><span class="sxs-lookup"><span data-stu-id="aa5e1-105">In .NET Framework 4.6.1, this app setting to disable RegEx usage was set to <code>false</code> by default.</span></span> <span data-ttu-id="aa5e1-106">A partir do .NET Framework 4.7.2, essa opção de configuração é definida como <code>true</code> por padrão para reduzir ainda mais a vulnerabilidade segura para aplicativos Web direcionados .NET Framework 4.7.2 e superior.</span><span class="sxs-lookup"><span data-stu-id="aa5e1-106">Starting with .NET Framework 4.7.2, this config switch is set to <code>true</code> by default to further reduce secure vulnerability for web applications that target .NET Framework 4.7.2 and above.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aa5e1-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="aa5e1-107">Suggestion</span></span>

<span data-ttu-id="aa5e1-108">Se observar que as expressões regulares em seu aplicativo Web não funcionam após atualizar para o .NET Framework 4.7.2, você poderá atualizar o valor da <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> configuração <code>false</code> para voltar ao comportamento anterior.</span><span class="sxs-lookup"><span data-stu-id="aa5e1-108">If you find that regular expressions in your web application do not work after upgrading to .NET Framework 4.7.2, you can update the value of the <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> setting to <code>false</code> to revert to the previous behavior.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="aa5e1-109">Nome</span><span class="sxs-lookup"><span data-stu-id="aa5e1-109">Name</span></span>    | <span data-ttu-id="aa5e1-110">Valor</span><span class="sxs-lookup"><span data-stu-id="aa5e1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aa5e1-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="aa5e1-111">Scope</span></span>   |<span data-ttu-id="aa5e1-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="aa5e1-112">Minor</span></span>|
|<span data-ttu-id="aa5e1-113">Versão</span><span class="sxs-lookup"><span data-stu-id="aa5e1-113">Version</span></span>|<span data-ttu-id="aa5e1-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="aa5e1-114">4.7.2</span></span>|
|<span data-ttu-id="aa5e1-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="aa5e1-115">Type</span></span>|<span data-ttu-id="aa5e1-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="aa5e1-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="aa5e1-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="aa5e1-117">Affected APIs</span></span>

<span data-ttu-id="aa5e1-118">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="aa5e1-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
