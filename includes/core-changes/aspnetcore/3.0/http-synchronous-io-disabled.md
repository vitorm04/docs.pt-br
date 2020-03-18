---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901683"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: IO síncrono desativado em todos os servidores

Começando com ASP.NET Core 3.0, as operações síncronas do servidor são desativadas por padrão.

#### <a name="change-description"></a>Descrição da alteração

`AllowSynchronousIO`é uma opção em cada servidor que ativa ou desativa APIs síncronas de IO como `HttpRequest.Body.Read`, `HttpResponse.Body.Write`e `Stream.Flush`. Essas APIs têm sido há muito uma fonte de fome de thread saem. A partir de ASP.NET Pré-visualização do Core 3.0 3, essas operações síncronas são desativadas por padrão.

Servidores afetados:

- Kestrel
- HttpSys
- IIS em processo
- TestServer

Espere erros semelhantes aos:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Cada servidor `AllowSynchronousIO` tem uma opção que controla esse comportamento `false`e o padrão para todos eles é agora .

O comportamento também pode ser substituído por solicitação como uma mitigação temporária. Por exemplo: 

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Se você tiver `TextWriter` problemas com um ou outro `Dispose`fluxo chamando `DisposeAsync` uma API síncrona, chame a nova API em vez disso.

Para discussão, consulte [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`e `Stream.Flush` foram permitidos por padrão.

#### <a name="new-behavior"></a>Novo comportamento

Essas APIs síncronas são proibidas por padrão:

Espere erros semelhantes aos:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Motivo da mudança

Essas APIs síncronas têm sido há muito uma fonte de fome de segmentos e travamentos de aplicativos. A partir ASP.NET pré-visualização do Núcleo 3.0, as operações síncronas são desativadas por padrão.

#### <a name="recommended-action"></a>Ação recomendada

Use as versões assíncronas dos métodos. O comportamento também pode ser substituído por solicitação como uma mitigação temporária.

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
