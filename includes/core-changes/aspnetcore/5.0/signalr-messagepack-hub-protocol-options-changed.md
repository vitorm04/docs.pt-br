---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507060"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="e9cc6-101">Signalr: tipo de opções de protocolo de Hub MessagePack alterado</span><span class="sxs-lookup"><span data-stu-id="e9cc6-101">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="e9cc6-102">O tipo de opções do protocolo Hub MessagePack do Signalr ASP.NET Core foi alterado de `IList<MessagePack.IFormatterResolver>` para o tipo da biblioteca [MessagePack](https://www.nuget.org/packages/MessagePack) `MessagePackSerializerOptions` .</span><span class="sxs-lookup"><span data-stu-id="e9cc6-102">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="e9cc6-103">Para discussão sobre essa alteração, consulte [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="e9cc6-103">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9cc6-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e9cc6-104">Version introduced</span></span>

<span data-ttu-id="e9cc6-105">5,0 versão prévia 4</span><span class="sxs-lookup"><span data-stu-id="e9cc6-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e9cc6-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="e9cc6-106">Old behavior</span></span>

<span data-ttu-id="e9cc6-107">Você pode adicionar às opções, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e9cc6-107">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="e9cc6-108">E substitua as opções da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e9cc6-108">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

#### <a name="new-behavior"></a><span data-ttu-id="e9cc6-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="e9cc6-109">New behavior</span></span>

<span data-ttu-id="e9cc6-110">Você pode adicionar às opções, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e9cc6-110">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="e9cc6-111">E substitua as opções da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e9cc6-111">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

#### <a name="reason-for-change"></a><span data-ttu-id="e9cc6-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="e9cc6-112">Reason for change</span></span>

<span data-ttu-id="e9cc6-113">Essa alteração faz parte da mudança para o MessagePack v2. x, que foi anunciado em [ASPNET/comunicados # 404](https://github.com/aspnet/Announcements/issues/404).</span><span class="sxs-lookup"><span data-stu-id="e9cc6-113">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="e9cc6-114">A biblioteca v2. x adicionou uma API de opções que é mais fácil de usar e fornece mais recursos do que a lista de `MessagePack.IFormatterResolver` que foi exposta antes.</span><span class="sxs-lookup"><span data-stu-id="e9cc6-114">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9cc6-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e9cc6-115">Recommended action</span></span>

<span data-ttu-id="e9cc6-116">Essa alteração significativa afeta qualquer pessoa que esteja Configurando valores <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="e9cc6-116">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="e9cc6-117">Se você estiver usando o protocolo ASP.NET Core de Hub MessagePack Signalr e modificando as opções, atualize seu uso para usar a nova API de opções, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="e9cc6-117">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

#### <a name="category"></a><span data-ttu-id="e9cc6-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="e9cc6-118">Category</span></span>

<span data-ttu-id="e9cc6-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e9cc6-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9cc6-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e9cc6-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
