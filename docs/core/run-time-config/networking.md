---
title: Definições de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802767"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="de995-103">Opções de configuração de tempo de execução para rede</span><span class="sxs-lookup"><span data-stu-id="de995-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="de995-104">Protocolo HTTP/2</span><span class="sxs-lookup"><span data-stu-id="de995-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="de995-105">Configura se o suporte para o protocolo HTTP/2 está habilitado.</span><span class="sxs-lookup"><span data-stu-id="de995-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="de995-106">Padrão: desabilitado (`false`).</span><span class="sxs-lookup"><span data-stu-id="de995-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="de995-107">Introduzido no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="de995-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="de995-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="de995-108">Setting name</span></span> | <span data-ttu-id="de995-109">Valores</span><span class="sxs-lookup"><span data-stu-id="de995-109">Values</span></span> |
| - | - |
| <span data-ttu-id="de995-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="de995-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="de995-111">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="de995-111">`false` - disabled</span></span><br/><span data-ttu-id="de995-112">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="de995-112">`true` - enabled</span></span> |
| <span data-ttu-id="de995-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="de995-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="de995-114">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="de995-114">`0` - disabled</span></span><br/><span data-ttu-id="de995-115">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="de995-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="de995-116">Manipulador HTTP de soquetes</span><span class="sxs-lookup"><span data-stu-id="de995-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="de995-117">Define se as APIs de rede de alto nível, como <xref:System.Net.Http.HttpClient>, usam <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou a implementação de <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> com base em [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="de995-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="de995-118">Padrão: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span><span class="sxs-lookup"><span data-stu-id="de995-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="de995-119">Você pode definir essa configuração programaticamente chamando o método <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de995-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="de995-120">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="de995-120">Setting name</span></span> | <span data-ttu-id="de995-121">Valores</span><span class="sxs-lookup"><span data-stu-id="de995-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="de995-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="de995-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="de995-123">`true`-habilita o uso de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="de995-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="de995-124">`false`-habilita o uso de <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="de995-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="de995-125">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="de995-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="de995-126">`1`-habilita o uso de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="de995-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="de995-127">`0`-habilita o uso de <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="de995-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
