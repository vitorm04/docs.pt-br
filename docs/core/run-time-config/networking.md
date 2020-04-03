---
title: Configurações de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: f5ea47f0444a911dc2347a66817cabf585fd8e70
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635418"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="d101f-103">Opções de configuração em tempo de execução para rede</span><span class="sxs-lookup"><span data-stu-id="d101f-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="d101f-104">Protocolo HTTP/2</span><span class="sxs-lookup"><span data-stu-id="d101f-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="d101f-105">Configura se o suporte para o protocolo HTTP/2 está ativado.</span><span class="sxs-lookup"><span data-stu-id="d101f-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="d101f-106">Padrão: Desabilitado ( ).`false`</span><span class="sxs-lookup"><span data-stu-id="d101f-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="d101f-107">Introduzido no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d101f-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="d101f-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="d101f-108">Setting name</span></span> | <span data-ttu-id="d101f-109">Valores</span><span class="sxs-lookup"><span data-stu-id="d101f-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d101f-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="d101f-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="d101f-111">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="d101f-111">`false` - disabled</span></span><br/><span data-ttu-id="d101f-112">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="d101f-112">`true` - enabled</span></span> |
| <span data-ttu-id="d101f-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="d101f-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="d101f-114">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="d101f-114">`0` - disabled</span></span><br/><span data-ttu-id="d101f-115">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="d101f-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="d101f-116">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="d101f-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="d101f-117">Configura se apis de rede de <xref:System.Net.Http.HttpClient>alto <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nível, como <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> , uso ou a implementação do que é baseado em [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="d101f-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="d101f-118">Padrão: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Uso`true`( ).</span><span class="sxs-lookup"><span data-stu-id="d101f-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="d101f-119">Você pode configurar esta configuração programática, chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="d101f-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="d101f-120">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="d101f-120">Setting name</span></span> | <span data-ttu-id="d101f-121">Valores</span><span class="sxs-lookup"><span data-stu-id="d101f-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d101f-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="d101f-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="d101f-123">`true`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="d101f-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="d101f-124">`false`- permite o uso de<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="d101f-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="d101f-125">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="d101f-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="d101f-126">`1`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="d101f-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="d101f-127">`0`- permite o uso de<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="d101f-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |

> [!NOTE]
> <span data-ttu-id="d101f-128">A partir de .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="d101f-128">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
