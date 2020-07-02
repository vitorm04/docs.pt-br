---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619763"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="8cd11-101">A propriedade HttpRequest.ContentEncoding proíbe a UTF7</span><span class="sxs-lookup"><span data-stu-id="8cd11-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="8cd11-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8cd11-102">Details</span></span>

<span data-ttu-id="8cd11-103">A partir do .NET Framework 4.5, a codificação UTF-7 está proibida nos corpos de <xref:System.Web.HttpRequest?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="8cd11-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="8cd11-104">Os dados para aplicativos que dependem de dados de entrada UTF-7 não serão decodificados corretamente em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="8cd11-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8cd11-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8cd11-105">Suggestion</span></span>

<span data-ttu-id="8cd11-106">De modo ideal, os aplicativos devem ser atualizados para não usar a codificação UTF-7 em <xref:System.Web.HttpRequest?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="8cd11-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="8cd11-107">De modo alternativo, o comportamento herdado pode ser restaurado usando o atributo <code>aspnet:AllowUtf7RequestContentEncoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8cd11-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="8cd11-108">Name</span><span class="sxs-lookup"><span data-stu-id="8cd11-108">Name</span></span>    | <span data-ttu-id="8cd11-109">Valor</span><span class="sxs-lookup"><span data-stu-id="8cd11-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8cd11-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="8cd11-110">Scope</span></span>   |<span data-ttu-id="8cd11-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8cd11-111">Edge</span></span>|
|<span data-ttu-id="8cd11-112">Versão</span><span class="sxs-lookup"><span data-stu-id="8cd11-112">Version</span></span>|<span data-ttu-id="8cd11-113">4.5</span><span class="sxs-lookup"><span data-stu-id="8cd11-113">4.5</span></span>|
|<span data-ttu-id="8cd11-114">Type</span><span class="sxs-lookup"><span data-stu-id="8cd11-114">Type</span></span>|<span data-ttu-id="8cd11-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="8cd11-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8cd11-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8cd11-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
