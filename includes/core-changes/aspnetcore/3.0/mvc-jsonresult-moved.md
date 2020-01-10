---
ms.openlocfilehash: 4f2ace670884d154b219d2146a242d2cee098831
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344301"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult movido para Microsoft. AspNetCore. Mvc. Core

`JsonResult` foi movido para o assembly `Microsoft.AspNetCore.Mvc.Core`. Esse tipo costumava ser definido em [Microsoft. AspNetCore. Mvc. Formatters. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Um atributo de nível de assembly [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) foi adicionado ao `Microsoft.AspNetCore.Mvc.Formatters.Json` para resolver esse problema para a maioria dos usuários. Aplicativos que usam bibliotecas de terceiros podem encontrar problemas.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 6

#### <a name="old-behavior"></a>Comportamento antigo

Um aplicativo que usa uma biblioteca baseada em 2,2 é compilado com êxito.

#### <a name="new-behavior"></a>Novo comportamento

Um aplicativo que usa uma biblioteca com base em 2,2 falha na compilação. Um erro contendo uma variação do texto a seguir é fornecido:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Para obter um exemplo desse problema, consulte [ASPNET/AspNetCore # 7220](https://github.com/aspnet/AspNetCore/issues/7220).

#### <a name="reason-for-change"></a>Motivo da alteração

Alterações no nível da plataforma para a composição de ASP.NET Core conforme descrito em [ASPNET/comunicados # 325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Ação recomendada

Bibliotecas compiladas na versão 2,2 do `Microsoft.AspNetCore.Mvc.Formatters.Json` talvez precisem ser recompiladas para resolver o problema de todos os consumidores. Se for afetado, contate o autor da biblioteca. Solicite a recompilação da biblioteca para o destino ASP.NET Core 3,0.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
