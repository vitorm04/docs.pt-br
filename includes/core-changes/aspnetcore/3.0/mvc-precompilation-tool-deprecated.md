---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901763"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: Ferramenta de pré-compilação depreciada

Em ASP.NET Core 1.1, o `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` pacote (ferramenta de pré-compilação MVC) foi introduzido para adicionar suporte para compilação em tempo de publicação de arquivos Razor (arquivos *.cshtml).* Em ASP.NET Core 2.1, o [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) foi introduzido para expandir os recursos da ferramenta de pré-compilação. O Razor SDK adicionou suporte para compilação de build e publish-time de arquivos Razor. O SDK verifica a correção de arquivos *.cshtml* no tempo de compilação enquanto melhora no tempo de inicialização do aplicativo. O Razor SDK está ligado por padrão, e nenhum gesto é necessário para começar a usá-lo.

Em ASP.NET Core 3.0, a ferramenta de pré-compilação MVC do ASP.NET Core 1.1 foi removida. As versões anteriores do pacote continuarão recebendo correções importantes de bugs e segurança na versão do patch.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` pacote foi usado para pré-compilar vistas MVC Razor.

#### <a name="new-behavior"></a>Novo comportamento

O Razor SDK suporta nativamente essa funcionalidade. O `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` pacote não é mais atualizado.

#### <a name="reason-for-change"></a>Motivo da mudança

O Razor SDK fornece mais funcionalidade e verifica a correção de arquivos *.cshtml* no momento da compilação. O SDK também melhora o tempo de inicialização do aplicativo.

#### <a name="recommended-action"></a>Ação recomendada

Para usuários de ASP.NET Core 2.1 ou posterior, atualize para usar o suporte nativo para pré-compilação no [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Se bugs ou recursos ausentes impedirem a migração para o Razor SDK, abra um problema no [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

### Affected APIs

Not detectable via API analysis

-->
