---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391176"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões

Em ASP.NET Core 5.0, o valor do cabeçalho de resposta `Content-Type` padrão que o Static File [Middleware](/aspnet/core/fundamentals/static-files) usa para arquivos *.csv* foi alterado para o valor `text/csv`compatível com os padrões .

Para discussão sobre este assunto, consulte [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).

#### <a name="version-introduced"></a>Versão introduzida

5.0 Visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

O `Content-Type` valor `application/octet-stream` do cabeçalho foi usado.

#### <a name="new-behavior"></a>Novo comportamento

O `Content-Type` valor `text/csv` do cabeçalho é usado.

#### <a name="reason-for-change"></a>Motivo da mudança

Conformidade com a norma [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)

#### <a name="recommended-action"></a>Ação recomendada

Se essa alteração impactar seu aplicativo, você pode personalizar o mapeamento do tipo extensão de arquivo para MIME. Para reverter `application/octet-stream` para o tipo <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> MIME, `Startup.Configure`modifique a chamada do método . Por exemplo: 

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Para obter mais informações sobre a personalização do mapeamento, consulte [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
