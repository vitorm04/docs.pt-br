---
title: Configurações de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989097"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="04f4b-103">Opções de configuração em tempo de execução para rede</span><span class="sxs-lookup"><span data-stu-id="04f4b-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="04f4b-104">Protocolo HTTP/2</span><span class="sxs-lookup"><span data-stu-id="04f4b-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="04f4b-105">Configura se o suporte para o protocolo HTTP/2 está ativado.</span><span class="sxs-lookup"><span data-stu-id="04f4b-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="04f4b-106">Padrão: Desabilitado ( ).`false`</span><span class="sxs-lookup"><span data-stu-id="04f4b-106">Default: Disabled (`false`).</span></span>

- <span data-ttu-id="04f4b-107">Introduzido no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="04f4b-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="04f4b-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="04f4b-108">Setting name</span></span> | <span data-ttu-id="04f4b-109">Valores</span><span class="sxs-lookup"><span data-stu-id="04f4b-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04f4b-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="04f4b-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="04f4b-111">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="04f4b-111">`false` - disabled</span></span><br/><span data-ttu-id="04f4b-112">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="04f4b-112">`true` - enabled</span></span> |
| <span data-ttu-id="04f4b-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="04f4b-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="04f4b-114">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="04f4b-114">`0` - disabled</span></span><br/><span data-ttu-id="04f4b-115">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="04f4b-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="04f4b-116">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="04f4b-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="04f4b-117">Configura se <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> usa ou empilha<xref:System.Net.Http.WinHttpHandler> de protocoloHTTP mais antigo (no Windows e, `CurlHandler`uma classe interna implementada em cima do [libcurl](https://curl.haxx.se/libcurl/), no Linux).</span><span class="sxs-lookup"><span data-stu-id="04f4b-117">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="04f4b-118">Você pode estar usando APIs de rede de alto <xref:System.Net.Http.HttpClientHandler> nível em vez de instanciar diretamente a classe.</span><span class="sxs-lookup"><span data-stu-id="04f4b-118">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="04f4b-119">Essa configuração também afeta a pilha de protocolos HTTP que <xref:System.Net.Http.HttpClient> é usada por APIs de rede de alto nível, incluindo e [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span><span class="sxs-lookup"><span data-stu-id="04f4b-119">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="04f4b-120">Padrão: <xref:System.Net.Http.SocketsHttpHandler> Uso`true`( ).</span><span class="sxs-lookup"><span data-stu-id="04f4b-120">Default: Use <xref:System.Net.Http.SocketsHttpHandler> (`true`).</span></span>

- <span data-ttu-id="04f4b-121">Você pode configurar esta configuração programática, chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="04f4b-121">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="04f4b-122">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="04f4b-122">Setting name</span></span> | <span data-ttu-id="04f4b-123">Valores</span><span class="sxs-lookup"><span data-stu-id="04f4b-123">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04f4b-124">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="04f4b-124">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="04f4b-125">`true`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="04f4b-125">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="04f4b-126">`false`- permite o <xref:System.Net.Http.WinHttpHandler> uso de no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux</span><span class="sxs-lookup"><span data-stu-id="04f4b-126">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="04f4b-127">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="04f4b-127">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="04f4b-128">`1`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="04f4b-128">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="04f4b-129">`0`- permite o <xref:System.Net.Http.WinHttpHandler> uso de no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux</span><span class="sxs-lookup"><span data-stu-id="04f4b-129">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="04f4b-130">A partir de .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="04f4b-130">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
