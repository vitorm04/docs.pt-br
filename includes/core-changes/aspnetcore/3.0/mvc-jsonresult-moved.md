---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901613"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult mudou-se para Microsoft.AspNetCore.Mvc.Core

`JsonResult`mudou-se `Microsoft.AspNetCore.Mvc.Core` para a assembléia. Este tipo costumava ser definido em [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Um atributo de nível de montagem [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) foi adicionado para `Microsoft.AspNetCore.Mvc.Formatters.Json` resolver esse problema para a maioria dos usuários. Aplicativos que usam bibliotecas de terceiros podem encontrar problemas.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Pré-visualização 6

#### <a name="old-behavior"></a>Comportamento antigo

Um aplicativo usando uma biblioteca baseada em 2.2 é criado com sucesso.

#### <a name="new-behavior"></a>Novo comportamento

Um aplicativo usando uma biblioteca baseada em 2.2 falha na compilação. Um erro contendo uma variação do seguinte texto é fornecido:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Para um exemplo de tal problema, consulte [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Motivo da mudança

Alterações no nível da plataforma na composição do ASP.NET Core conforme descrito em [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Ação recomendada

Bibliotecas compiladas em relação à `Microsoft.AspNetCore.Mvc.Formatters.Json` versão 2.2 podem precisar recompilar para resolver o problema para todos os consumidores. Se for afetado, entre em contato com o autor da biblioteca. Solicite recompilação da biblioteca para atingir ASP.NET Núcleo 3.0.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
