---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901585"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autorização: IAllowAnonymous removido do AuthorizationFilterContext.Filters

A partir de ASP.NET O Núcleo 3.0, o MVC não adiciona [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) para [atributos [AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) que foram descobertos em controladores e métodos de ação. Esta mudança é tratada localmente <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>para derivativos de , <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> mas é uma mudança de ruptura para e implementações. Tais implementações envoltas em um atributo [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) são uma maneira [popular](https://stackoverflow.com/a/41348219/608220) e suportada para obter uma autorização fortemente digitada, baseada em atributos, quando tanto a configuração quanto a injeção de dependência são necessárias.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>apareceu na coleção [AuthorizationFilterContext.Filters.](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) O teste para a presença da interface foi uma abordagem válida para substituir ou desativar o filtro em métodos individuais de controlador.

#### <a name="new-behavior"></a>Novo comportamento

`IAllowAnonymous`não aparece mais `AuthorizationFilterContext.Filters` na coleção. `IAsyncAuthorizationFilter`implementações que dependem do comportamento antigo normalmente causam respostas intermitentes HTTP 401 Não Autorizadas ou HTTP 403 Proibidas.

#### <a name="reason-for-change"></a>Motivo da mudança

Uma nova estratégia de roteamento de ponto final foi introduzida no ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Ação recomendada

Pesquise os metadados `IAllowAnonymous`do ponto final para . Por exemplo: 

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Um exemplo dessa técnica é visto [neste método HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!--

#### Affected APIs

Not detectable via API analysis

-->
