---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391176"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="90101-101">Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões</span><span class="sxs-lookup"><span data-stu-id="90101-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="90101-102">Em ASP.NET Core 5.0, o valor do cabeçalho de resposta `Content-Type` padrão que o Static File [Middleware](/aspnet/core/fundamentals/static-files) usa para arquivos *.csv* foi alterado para o valor `text/csv`compatível com os padrões .</span><span class="sxs-lookup"><span data-stu-id="90101-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="90101-103">Para discussão sobre este assunto, consulte [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="90101-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="90101-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="90101-104">Version introduced</span></span>

<span data-ttu-id="90101-105">5.0 Visualização 1</span><span class="sxs-lookup"><span data-stu-id="90101-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="90101-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="90101-106">Old behavior</span></span>

<span data-ttu-id="90101-107">O `Content-Type` valor `application/octet-stream` do cabeçalho foi usado.</span><span class="sxs-lookup"><span data-stu-id="90101-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="90101-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="90101-108">New behavior</span></span>

<span data-ttu-id="90101-109">O `Content-Type` valor `text/csv` do cabeçalho é usado.</span><span class="sxs-lookup"><span data-stu-id="90101-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="90101-110">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="90101-110">Reason for change</span></span>

<span data-ttu-id="90101-111">Conformidade com a norma [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)</span><span class="sxs-lookup"><span data-stu-id="90101-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="90101-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="90101-112">Recommended action</span></span>

<span data-ttu-id="90101-113">Se essa alteração impactar seu aplicativo, você pode personalizar o mapeamento do tipo extensão de arquivo para MIME.</span><span class="sxs-lookup"><span data-stu-id="90101-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="90101-114">Para reverter `application/octet-stream` para o tipo <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> MIME, `Startup.Configure`modifique a chamada do método .</span><span class="sxs-lookup"><span data-stu-id="90101-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="90101-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="90101-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="90101-116">Para obter mais informações sobre a personalização do mapeamento, consulte [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="90101-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="90101-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="90101-117">Category</span></span>

<span data-ttu-id="90101-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="90101-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90101-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="90101-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
