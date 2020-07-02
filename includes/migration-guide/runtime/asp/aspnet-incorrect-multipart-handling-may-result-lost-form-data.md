---
ms.openlocfilehash: 135d59de135c8416d384b221379f912c8a9172ad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621908"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="26c2c-101">ASP.NET A manipulação incorreta com várias partes pode resultar na perda dos dados de formulário.</span><span class="sxs-lookup"><span data-stu-id="26c2c-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="26c2c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="26c2c-102">Details</span></span>

<span data-ttu-id="26c2c-103">Nos aplicativos que direcionam o .NET Framework 4.7.2 e versões anteriores, o ASP.Net pode analisar incorretamente valores de limite com várias partes, resultando na indisponibilidade dos dados de formulário durante a execução da solicitação.</span><span class="sxs-lookup"><span data-stu-id="26c2c-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="26c2c-104">Os aplicativos que direcionam o .NET Framework 4.8 ou versões posteriores analisam corretamente os dados com várias partes para que os valores de formulário estejam disponíveis durante a execução da solicitação.</span><span class="sxs-lookup"><span data-stu-id="26c2c-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="26c2c-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="26c2c-105">Suggestion</span></span>

<span data-ttu-id="26c2c-106">Começando com aplicativos em execução no .NET Framework 4.8, ao direcionar o .NET Framework 4.8 ou posterior usando o elemento <code>targetFrameworkVersion</code>, o comportamento padrão é alterado para retirar os delimitadores.</span><span class="sxs-lookup"><span data-stu-id="26c2c-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="26c2c-107">Ao direcionar versões anteriores da estrutura ou não usar <code>targetFrameworkVersion</code>, ainda são retornados delimitadores à direita para alguns valores. Esse comportamento também pode ser explicitamente controlado com um <code>appSetting</code>:</span><span class="sxs-lookup"><span data-stu-id="26c2c-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="26c2c-108">Name</span><span class="sxs-lookup"><span data-stu-id="26c2c-108">Name</span></span>    | <span data-ttu-id="26c2c-109">Valor</span><span class="sxs-lookup"><span data-stu-id="26c2c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="26c2c-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="26c2c-110">Scope</span></span>   |<span data-ttu-id="26c2c-111">Unknown (desconhecido)</span><span class="sxs-lookup"><span data-stu-id="26c2c-111">Unknown</span></span>|
|<span data-ttu-id="26c2c-112">Versão</span><span class="sxs-lookup"><span data-stu-id="26c2c-112">Version</span></span>|<span data-ttu-id="26c2c-113">4.8</span><span class="sxs-lookup"><span data-stu-id="26c2c-113">4.8</span></span>|
|<span data-ttu-id="26c2c-114">Type</span><span class="sxs-lookup"><span data-stu-id="26c2c-114">Type</span></span>|<span data-ttu-id="26c2c-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="26c2c-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26c2c-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="26c2c-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
