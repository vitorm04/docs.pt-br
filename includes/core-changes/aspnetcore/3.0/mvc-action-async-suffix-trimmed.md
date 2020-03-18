---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901638"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: Sufixo assíncrono aparado a partir de nomes de ação do controlador

Como parte do endereçamento [do dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), `Async` ASP.NET MVC do Core apara o sufixo dos nomes de ação por padrão. Começando com ASP.NET Núcleo 3.0, essa alteração afeta tanto o roteamento quanto a geração de links.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Considere o seguinte controlador ASP.NET Core MVC:

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

A ação é rotável via `Product/ListAsync`. A geração de `Async` links requer especificação do sufixo. Por exemplo: 

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Novo comportamento

Em ASP.NET Núcleo 3.0, a ação `Product/List`é roteável via . O código de geração `Async` de links deve omitir o sufixo. Por exemplo: 

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Essa alteração não afeta nomes especificados usando o atributo. `[ActionName]` O novo comportamento pode `MvcOptions.SuppressAsyncSuffixInActionNames` ser `false` `Startup.ConfigureServices`desativado definindo em :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Motivo da mudança

Por convenção, os métodos assíncronos `Async`.NET são sufixos com . No entanto, quando um método define uma ação MVC, é indesejável usar o `Async` sufixo.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu aplicativo depender das ações de `Async` MVC que preservam o sufixo do nome, escolha uma das seguintes atenuações:

- Use `[ActionName]` o atributo para preservar o nome original.
- Desativar a renomeação inteiramente `false` `Startup.ConfigureServices`configurando `MvcOptions.SuppressAsyncSuffixInActionNames` para :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
