---
ms.openlocfilehash: ed669364efe9dd8f57d831a3764dd3fc68cd5e05
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497607"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="34693-101">ASP.NET A manipulação incorreta com várias partes pode resultar na perda dos dados de formulário.</span><span class="sxs-lookup"><span data-stu-id="34693-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="34693-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="34693-102">Details</span></span>

<span data-ttu-id="34693-103">Nos aplicativos que direcionam o .NET Framework 4.7.2 e versões anteriores, o ASP.Net pode analisar incorretamente valores de limite com várias partes, resultando na indisponibilidade dos dados de formulário durante a execução da solicitação.</span><span class="sxs-lookup"><span data-stu-id="34693-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="34693-104">Os aplicativos que direcionam o .NET Framework 4.8 ou versões posteriores analisam corretamente os dados com várias partes para que os valores de formulário estejam disponíveis durante a execução da solicitação.</span><span class="sxs-lookup"><span data-stu-id="34693-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="34693-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="34693-105">Suggestion</span></span>

<span data-ttu-id="34693-106">Começando com aplicativos em execução no .NET Framework 4.8, ao direcionar o .NET Framework 4.8 ou posterior usando o elemento <code>targetFrameworkVersion</code>, o comportamento padrão é alterado para retirar os delimitadores.</span><span class="sxs-lookup"><span data-stu-id="34693-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="34693-107">Ao direcionar versões anteriores da estrutura ou não usar <code>targetFrameworkVersion</code>, ainda são retornados delimitadores à direita para alguns valores. Esse comportamento também pode ser explicitamente controlado com um <code>appSetting</code>:</span><span class="sxs-lookup"><span data-stu-id="34693-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="34693-108">Nome</span><span class="sxs-lookup"><span data-stu-id="34693-108">Name</span></span>    | <span data-ttu-id="34693-109">Valor</span><span class="sxs-lookup"><span data-stu-id="34693-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="34693-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="34693-110">Scope</span></span>   |<span data-ttu-id="34693-111">Desconhecido</span><span class="sxs-lookup"><span data-stu-id="34693-111">Unknown</span></span>|
|<span data-ttu-id="34693-112">Versão</span><span class="sxs-lookup"><span data-stu-id="34693-112">Version</span></span>|<span data-ttu-id="34693-113">4.8</span><span class="sxs-lookup"><span data-stu-id="34693-113">4.8</span></span>|
|<span data-ttu-id="34693-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="34693-114">Type</span></span>|<span data-ttu-id="34693-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="34693-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="34693-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="34693-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
