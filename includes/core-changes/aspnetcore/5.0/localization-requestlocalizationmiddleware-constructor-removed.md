---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281325"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="974e8-101">Localização: Construtor obsoleto removido no middleware de localização de solicitação</span><span class="sxs-lookup"><span data-stu-id="974e8-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="974e8-102">O <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> Construtor que não tem um <xref:Microsoft.Extensions.Logging.ILoggerFactory> parâmetro foi marcado como obsoleto [nesta confirmação](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span><span class="sxs-lookup"><span data-stu-id="974e8-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="974e8-103">No ASP.NET Core 5,0, o Construtor obsoleto foi removido.</span><span class="sxs-lookup"><span data-stu-id="974e8-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="974e8-104">Para obter uma discussão, consulte [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="974e8-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="974e8-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="974e8-105">Version introduced</span></span>

<span data-ttu-id="974e8-106">5.0</span><span class="sxs-lookup"><span data-stu-id="974e8-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="974e8-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="974e8-107">Old behavior</span></span>

<span data-ttu-id="974e8-108">O `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Construtor obsoleto existe.</span><span class="sxs-lookup"><span data-stu-id="974e8-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="974e8-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="974e8-109">New behavior</span></span>

<span data-ttu-id="974e8-110">O `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Construtor obsoleto não existe.</span><span class="sxs-lookup"><span data-stu-id="974e8-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="974e8-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="974e8-111">Reason for change</span></span>

<span data-ttu-id="974e8-112">Essa alteração garante que o middleware de localização de solicitação sempre tenha acesso a um agente de log.</span><span class="sxs-lookup"><span data-stu-id="974e8-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="974e8-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="974e8-113">Recommended action</span></span>

<span data-ttu-id="974e8-114">Ao construir manualmente uma instância do `RequestLocalizationMiddleware` , passe uma `ILoggerFactory` instância no construtor.</span><span class="sxs-lookup"><span data-stu-id="974e8-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="974e8-115">Se uma `ILoggerFactory` instância válida não estiver disponível nesse contexto, considere passar o construtor de middleware uma <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instância.</span><span class="sxs-lookup"><span data-stu-id="974e8-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="974e8-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="974e8-116">Category</span></span>

<span data-ttu-id="974e8-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="974e8-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="974e8-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="974e8-118">Affected APIs</span></span>

[<span data-ttu-id="974e8-119">RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="974e8-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
