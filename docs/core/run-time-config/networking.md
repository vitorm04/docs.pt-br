---
title: Definições de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: d43b68206cc82f4a41df02bd5998702b4f5d0590
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538127"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="867ef-103">Opções de configuração de tempo de execução para rede</span><span class="sxs-lookup"><span data-stu-id="867ef-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="867ef-104">Protocolo HTTP/2</span><span class="sxs-lookup"><span data-stu-id="867ef-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="867ef-105">Configura se o suporte para o protocolo HTTP/2 está habilitado.</span><span class="sxs-lookup"><span data-stu-id="867ef-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="867ef-106">Se você omitir essa configuração, o suporte para o protocolo HTTP/2 será desabilitado.</span><span class="sxs-lookup"><span data-stu-id="867ef-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="867ef-107">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="867ef-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="867ef-108">Introduzido no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="867ef-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="867ef-109">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="867ef-109">Setting name</span></span> | <span data-ttu-id="867ef-110">Valores</span><span class="sxs-lookup"><span data-stu-id="867ef-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="867ef-111">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="867ef-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="867ef-112">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="867ef-112">`false` - disabled</span></span><br/><span data-ttu-id="867ef-113">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="867ef-113">`true` - enabled</span></span> |
| <span data-ttu-id="867ef-114">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="867ef-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="867ef-115">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="867ef-115">`0` - disabled</span></span><br/><span data-ttu-id="867ef-116">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="867ef-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="867ef-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="867ef-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="867ef-118">Configura se <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> o usa ou pilhas de protocolo http mais antigas ( <xref:System.Net.Http.WinHttpHandler> no Windows e `CurlHandler` uma classe interna implementada sobre [libcurl](https://curl.haxx.se/libcurl/), no Linux).</span><span class="sxs-lookup"><span data-stu-id="867ef-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="867ef-119">Você pode estar usando APIs de rede de alto nível em vez de instanciar diretamente a <xref:System.Net.Http.HttpClientHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="867ef-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="867ef-120">Essa configuração também afeta qual pilha de protocolo HTTP é usada por APIs de rede de alto nível, incluindo <xref:System.Net.Http.HttpClient> e [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span><span class="sxs-lookup"><span data-stu-id="867ef-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="867ef-121">Se você omitir essa configuração, o <xref:System.Net.Http.HttpClientHandler> usará <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="867ef-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="867ef-122">Isso é equivalente a definir o valor como `true` .</span><span class="sxs-lookup"><span data-stu-id="867ef-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="867ef-123">Você pode definir essa configuração programaticamente chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="867ef-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="867ef-124">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="867ef-124">Setting name</span></span> | <span data-ttu-id="867ef-125">Valores</span><span class="sxs-lookup"><span data-stu-id="867ef-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="867ef-126">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="867ef-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="867ef-127">`true` – habilita o uso de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="867ef-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="867ef-128">`false` – habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux</span><span class="sxs-lookup"><span data-stu-id="867ef-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="867ef-129">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="867ef-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="867ef-130">`1` – habilita o uso de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="867ef-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="867ef-131">`0` – habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux</span><span class="sxs-lookup"><span data-stu-id="867ef-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="867ef-132">A partir do .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="867ef-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
