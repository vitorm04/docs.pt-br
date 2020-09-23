---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077586"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Mais de: JSObjectReference e tipos JSInProcessObjectReference alterados para interno

Os novos `Microsoft.JSInterop.JSObjectReference` e os `Microsoft.JSInterop.JSInProcessObjectReference` tipos introduzidos no ASP.NET Core 5,0 RC1 foram marcados como `internal` .

#### <a name="version-introduced"></a>Versão introduzida

5,0 RC2

#### <a name="old-behavior"></a>Comportamento antigo

Um `JSObjectReference` pode ser obtido de uma chamada de interoperabilidade JavaScript por meio do `IJSRuntime` . Por exemplo:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a>Novo comportamento

`JSObjectReference` usa o modificador de acesso [interno](../../../../docs/csharp/language-reference/keywords/internal.md) . A `public` `IJSObjectReference` interface deve ser usada em seu lugar. Por exemplo:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` também foi marcado como `internal` e foi substituído por `IJSInProcessObjectReference` .

#### <a name="reason-for-change"></a>Motivo da alteração

A alteração torna o recurso de interoperabilidade JavaScript mais consistente com outros padrões no mais baixo. `IJSObjectReference` é análogo a `IJSRuntime` , pois ele atende a uma finalidade semelhante e tem métodos e extensões semelhantes.

#### <a name="recommended-action"></a>Ação recomendada

Substituir ocorrências de `JSObjectReference` e `JSInProcessObjectReference` por `IJSObjectReference` e `IJSInProcessObjectReference` , respectivamente.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
