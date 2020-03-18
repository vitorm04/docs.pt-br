---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344295"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: Compilação runtime mudou-se para um pacote

O suporte para compilação em tempo de execução de visualizações de navalha e páginas de barbear mudou-se para um pacote separado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

A compilação em tempo de execução está disponível sem precisar de pacotes adicionais.

#### <a name="new-behavior"></a>Novo comportamento

A funcionalidade foi transferida para o pacote [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)

As APIs a seguir `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` estavam disponíveis anteriormente para suportar compilação em tempo de execução. As APIs já `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`estão disponíveis via .

- `RazorViewEngineOptions.FileProviders` agora é `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` agora é `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Além disso, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` foi removido. A recompilação das alterações de arquivo `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` é habilitada por padrão, fazendo referência ao pacote.

#### <a name="reason-for-change"></a>Motivo da mudança

Essa mudança foi necessária para remover a dependência do núcleo de ASP.NET em Roslyn.

#### <a name="recommended-action"></a>Ação recomendada

Os aplicativos que requerem compilação em tempo de execução ou recompilação de arquivos Razor devem tomar as seguintes etapas:

1. Adicione uma referência `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` ao pacote.
1. Atualize o `Startup.ConfigureServices` método do projeto `AddRazorRuntimeCompilation`para incluir uma chamada para . Por exemplo: 

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
