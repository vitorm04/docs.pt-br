---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901667"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: Tipos de "pubternal" alterados para internos

Em ASP.NET Núcleo 3.0, todos os tipos "pubternais" `public` em MVC foram `internal` atualizados para estar em um namespace suportado ou conforme apropriado.

#### <a name="change-description"></a>Descrição da alteração

Em ASP.NET Core, os tipos "pubternais" são declarados como `public` mas residem em um `.Internal`espaço de nome sufixo. Embora esses `public`tipos sejam, eles não têm política de apoio e estão sujeitos a mudanças. Infelizmente, o uso acidental desses tipos tem sido comum, resultando em mudanças nesses projetos e limitando a capacidade de manter o quadro.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Alguns tipos em `public` MVC `.Internal` estavam em um namespace. Esses tipos não tinham política de apoio e estavam sujeitos a mudanças.

#### <a name="new-behavior"></a>Novo comportamento

Todos esses tipos são `public` atualizados para estar em `internal`um namespace suportado ou marcado como .

#### <a name="reason-for-change"></a>Motivo da mudança

O uso acidental dos tipos "pubternais" tem sido comum, resultando em mudanças nesses projetos e limitando a capacidade de manutenção da estrutura.

#### <a name="recommended-action"></a>Ação recomendada

Se você estiver usando tipos `public` que se tornaram verdadeiramente e foram movidos para um novo espaço de nome suportado, atualize suas referências para combinar com os novos namespaces.

Se você estiver usando tipos que `internal`se tornaram marcados como , você precisará encontrar uma alternativa. Os tipos anteriormente "pubternais" nunca foram apoiados para uso público. Se houver tipos específicos nesses namespaces que são críticos para seus aplicativos, arquive um problema no [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues). Podem ser feitas considerações para `public`a realização dos tipos solicitados.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Essa alteração inclui tipos nos seguintes namespaces:

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
