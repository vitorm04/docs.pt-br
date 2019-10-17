---
ms.openlocfilehash: ab7c097f6b65d539117e5a6ef38eb67b24695a32
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394351"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: e/s síncrona desabilitada em todos os servidores

A partir do ASP.NET Core 3,0, as operações de servidor síncronas são desabilitadas por padrão.

#### <a name="change-description"></a>Alterar descrição

`AllowSynchronousIO` é uma opção em cada servidor que habilita ou desabilita APIs de e/s síncronas como `HttpRequest.Body.Read`, `HttpResponse.Body.Write` e `Stream.Flush`. Essas APIs têm sido uma origem de privação de threads e bloqueios de aplicativo. A partir do ASP.NET Core 3,0 Preview 3, essas operações síncronas são desabilitadas por padrão.

Servidores afetados:

- Kestrel
- HttpSys
- IIS em processo
- TestServer

Esperar erros semelhantes a:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Cada servidor tem uma opção `AllowSynchronousIO` que controla esse comportamento e o padrão para todos eles agora é `false`.

O comportamento também pode ser substituído em uma base por solicitação como uma mitigação temporária. Por exemplo:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Se você tiver problemas com um `TextWriter` ou outro fluxo chamando uma API síncrona no `Dispose`, chame a nova API `DisposeAsync` em vez disso.

Para obter uma discussão, consulte [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

os `HttpRequest.Body.Read`, `HttpResponse.Body.Write` e `Stream.Flush` eram permitidos por padrão.

#### <a name="new-behavior"></a>Novo comportamento

Essas APIs síncronas não são permitidas por padrão: 

Esperar erros semelhantes a:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Motivo da alteração

Essas APIs síncronas têm sido uma origem de privação de threads e bloqueios de aplicativo. A partir do ASP.NET Core 3,0 Preview 3, as operações síncronas são desabilitadas por padrão.

#### <a name="recommended-action"></a>Ação recomendada

Use as versões assíncronas dos métodos. O comportamento também pode ser substituído em uma base por solicitação como uma mitigação temporária.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
