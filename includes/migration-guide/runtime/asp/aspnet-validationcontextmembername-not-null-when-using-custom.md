---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621907"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="149db-101">ASP.NET ValidationContext.MemberName não é NULL ao usar o DataAnnotations.ValidationAttribute personalizado</span><span class="sxs-lookup"><span data-stu-id="149db-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="149db-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="149db-102">Details</span></span>

<span data-ttu-id="149db-103">No .NET Framework 4.7.2 e versões anteriores, ao usar um <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personalizado, a propriedade <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="149db-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="149db-104">Na versão .NET Framework 4,8 anterior à atualização de outubro de 2019, ela retorna o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="149db-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="149db-105">Começando com [.NET Framework visualização de outubro de 2019 de Rollup de qualidade](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) para .NET Framework 4,8, ele retorna `null` por padrão, mas você pode optar por retornar o nome do membro em vez disso.</span><span class="sxs-lookup"><span data-stu-id="149db-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="149db-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="149db-106">Suggestion</span></span>

<span data-ttu-id="149db-107">Adicione a configuração a seguir ao arquivo *web.config* para que a propriedade retorne o nome do membro em [.NET Framework visualização de outubro de 2019 de Rollup de qualidade](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) para .NET Framework 4,8 e versões posteriores:</span><span class="sxs-lookup"><span data-stu-id="149db-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="149db-108">Na versão .NET Framework 4,8 anterior à atualização de outubro de 2019, adicionar isso ao arquivo de *web.config* restaura o comportamento anterior e a propriedade retorna `null` .</span><span class="sxs-lookup"><span data-stu-id="149db-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="149db-109">Name</span><span class="sxs-lookup"><span data-stu-id="149db-109">Name</span></span>    | <span data-ttu-id="149db-110">Valor</span><span class="sxs-lookup"><span data-stu-id="149db-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="149db-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="149db-111">Scope</span></span>   |<span data-ttu-id="149db-112">Unknown (desconhecido)</span><span class="sxs-lookup"><span data-stu-id="149db-112">Unknown</span></span>|
|<span data-ttu-id="149db-113">Versão</span><span class="sxs-lookup"><span data-stu-id="149db-113">Version</span></span>|<span data-ttu-id="149db-114">4.8</span><span class="sxs-lookup"><span data-stu-id="149db-114">4.8</span></span>|
|<span data-ttu-id="149db-115">Type</span><span class="sxs-lookup"><span data-stu-id="149db-115">Type</span></span>|<span data-ttu-id="149db-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="149db-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="149db-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="149db-117">Affected APIs</span></span>

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
