---
ms.openlocfilehash: 503d61cb86c83e2f32ad40c60a127ae255ef71b0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198337"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: sufixo assíncrono cortado dos nomes de ação do controlador

Como parte do endereçamento [ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC apara o sufixo `Async` dos nomes de ação por padrão. A partir do ASP.NET Core 3,0, essa alteração afeta o roteamento e a geração de link.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Considere o seguinte controlador MVC ASP.NET Core:

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

A ação é roteável via `Product/ListAsync`. A geração de link requer a especificação do sufixo `Async`. Por exemplo:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Novo comportamento

No ASP.NET Core 3,0, a ação é roteável via `Product/List`. O código de geração de link deve omitir o sufixo `Async`. Por exemplo:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Essa alteração não afeta os nomes especificados usando o atributo `[ActionName]`. O novo comportamento pode ser desabilitado definindo `MvcOptions.SuppressAsyncSuffixInActionNames` como `false` em `Startup.ConfigureServices`:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Motivo da alteração

Por convenção, os métodos .NET assíncronos têm um sufixo `Async`. No entanto, quando um método define uma ação MVC, não é desejável usar o sufixo `Async`.

#### <a name="recommended-action"></a>Ação recomendada

Se seu aplicativo depende de ações do MVC preservando o sufixo `Async` do nome, escolha uma das seguintes atenuações:

- Use o atributo `[ActionName]` para preservar o nome original.
- Desabilite a renomeação total definindo `MvcOptions.SuppressAsyncSuffixInActionNames` como `false` em `Startup.ConfigureServices`:

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
