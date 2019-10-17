---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394425"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: tipos "Pubternal" alterados para interno

No ASP.NET Core 3,0, todos os tipos "pubternal" no MVC foram atualizados para `public` em um namespace com suporte ou `internal`, conforme apropriado.

#### <a name="change-description"></a>Alterar descrição

Em ASP.NET Core, os tipos "pubternal" são declarados como `public`, mas residem em um namespace `.Internal`. Embora esses tipos sejam `public`, eles não têm nenhuma política de suporte e estão sujeitos a alterações significativas. Infelizmente, o uso acidental desses tipos foi comum, resultando em alterações significativas nesses projetos e limitando a capacidade de manter a estrutura.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Alguns tipos no MVC foram `public`, mas em um namespace `.Internal`. Esses tipos não tinham nenhuma política de suporte e estavam sujeitos a alterações significativas.

#### <a name="new-behavior"></a>Novo comportamento

Todos esses tipos são atualizados para serem `public` em um namespace com suporte ou marcados como `internal`.

#### <a name="reason-for-change"></a>Motivo da alteração

O uso acidental dos tipos "pubternal" é comum, resultando em alterações significativas nesses projetos e limitando a capacidade de manter a estrutura.

#### <a name="recommended-action"></a>Ação recomendada

Se você estiver usando tipos que se tornaram verdadeiramente `public` e foram movidos para um novo namespace com suporte, atualize suas referências para que correspondam aos novos namespaces.

Se você estiver usando tipos que se tornaram marcados como `internal`, você precisará encontrar uma alternativa. Os tipos de "pubternal" anteriormente nunca tinham suporte para uso público. Se houver tipos específicos nesses namespaces que são críticos para seus aplicativos, execute um problema em [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues). Podem ser feitas considerações para fazer os tipos solicitados `public`.

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
