---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291662"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UseSignalR e UseConnections métodos removidos

Em ASP.NET Núcleo 3.0, o SignalR adotou o roteamento de ponto final. Como parte dessa mudança, os <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>métodos <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>relacionados foram marcados como obsoletos. Em ASP.NET Núcleo 5.0, esses métodos obsoletos foram removidos. Para obter a lista completa de métodos, consulte [APIs afetados](#affected-apis).

Para discussão sobre este assunto, consulte [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).

#### <a name="version-introduced"></a>Versão introduzida

5.0 Pré-visualização 3

#### <a name="old-behavior"></a>Comportamento antigo

Os hubs SignalR e os manipuladores de conexão `UseSignalR` `UseConnections` podem ser registrados no pipeline de middleware usando os métodos ou.

#### <a name="new-behavior"></a>Novo comportamento

Os hubs SignalR e os manipuladores <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> de <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> conexão <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>devem ser registrados dentro <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> dos métodos de extensão e de extensão em .

#### <a name="reason-for-change"></a>Motivo da mudança

Os métodos antigos tinham lógica de roteamento personalizado que não interagia com outros componentes de roteamento no ASP.NET Core. Em ASP.NET Core 3.0, um novo sistema de roteamento de uso geral, chamado de roteamento de ponto final, foi introduzido. O roteamento de ponto final permitiu que o SignalR interagisse com outros componentes de roteamento. Mudar para este modelo permite que os usuários percebam todos os benefícios do roteamento de ponto final. Consequentemente, os métodos antigos foram removidos.

#### <a name="recommended-action"></a>Ação recomendada

Remova o `UseSignalR` código `UseConnections` que chama `Startup.Configure` ou do método do seu projeto. Substitua-o `MapHub` por `MapConnectionHandler`chamadas para ou, respectivamente, `UseEndpoints`dentro do corpo de uma chamada para . Por exemplo: 

**Código antigo:**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**Novo código:**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

Em geral, `MapHub` suas `MapConnectionHandler` chamadas anteriores e podem `UseSignalR` `UseConnections` ser `UseEndpoints` transferidas diretamente do corpo de e para com pouca ou nenhuma mudança necessária.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
