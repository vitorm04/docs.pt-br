---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391176"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões

No ASP.NET Core 5,0, o `Content-Type` valor de cabeçalho de resposta padrão que o middleware de [arquivo estático](/aspnet/core/fundamentals/static-files) usa para arquivos *. csv* foi alterado para o valor em conformidade com os padrões `text/csv` .

Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).

#### <a name="version-introduced"></a>Versão introduzida

5,0 visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

O `Content-Type` valor do cabeçalho `application/octet-stream` foi usado.

#### <a name="new-behavior"></a>Novo comportamento

O `Content-Type` valor do cabeçalho `text/csv` é usado.

#### <a name="reason-for-change"></a>Motivo da alteração

Conformidade com o padrão [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) .

#### <a name="recommended-action"></a>Ação recomendada

Se essa alteração impactar seu aplicativo, você poderá personalizar o mapeamento de tipo de extensão para MIME do arquivo. Para reverter para o `application/octet-stream` tipo MIME, modifique a <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> chamada do método em `Startup.Configure` . Por exemplo:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Para obter mais informações sobre como personalizar o mapeamento, consulte [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
