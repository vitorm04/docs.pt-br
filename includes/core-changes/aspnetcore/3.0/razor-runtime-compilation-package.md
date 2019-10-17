---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394068"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: compilação de tempo de execução movida para um pacote

O suporte para a compilação em tempo de execução de exibições do Razor e Razor Pages foi movido para um pacote separado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

A compilação em tempo de execução está disponível sem a necessidade de pacotes adicionais.

#### <a name="new-behavior"></a>Novo comportamento

A funcionalidade foi movida para o pacote `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

As APIs a seguir estavam disponíveis anteriormente no `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` para dar suporte à compilação em tempo de execução. As APIs agora estão disponíveis por meio de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Além disso, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` foi removido. A recompilação em alterações de arquivo é habilitada por padrão referenciando o pacote `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração foi necessária para remover a dependência de estrutura compartilhada ASP.NET Core em Roslyn.

#### <a name="recommended-action"></a>Ação recomendada

Aplicativos que exigem compilação em tempo de execução ou recompilação de arquivos Razor devem executar as seguintes etapas:

1. Adicione uma referência ao pacote `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.
1. Atualize o método `Startup.ConfigureServices` do projeto para incluir uma chamada para `AddMvcRazorRuntimeCompilation`. Por exemplo, em `Startup.ConfigureServices`:

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
