---
title: Definições de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188296"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="5852a-103">Opções de configuração de tempo de execução para rede</span><span class="sxs-lookup"><span data-stu-id="5852a-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="5852a-104">Protocolo HTTP/2</span><span class="sxs-lookup"><span data-stu-id="5852a-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="5852a-105">Configura se o suporte para o protocolo HTTP/2 está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5852a-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="5852a-106">Introduzido no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5852a-106">Introduced in .NET Core 3.0.</span></span>

- <span data-ttu-id="5852a-107">Somente .NET Core 3,0: se você omitir essa configuração, o suporte para o protocolo HTTP/2 será desabilitado.</span><span class="sxs-lookup"><span data-stu-id="5852a-107">.NET Core 3.0 only: If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="5852a-108">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="5852a-108">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="5852a-109">.NET Core 3,1 e .NET 5 +: se você omitir essa configuração, o suporte para o protocolo HTTP/2 será habilitado.</span><span class="sxs-lookup"><span data-stu-id="5852a-109">.NET Core 3.1 and .NET 5+: If you omit this setting, support for the HTTP/2 protocol is enabled.</span></span> <span data-ttu-id="5852a-110">Isso é equivalente a definir o valor como `true` .</span><span class="sxs-lookup"><span data-stu-id="5852a-110">This is equivalent to setting the value to `true`.</span></span>

| | <span data-ttu-id="5852a-111">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5852a-111">Setting name</span></span> | <span data-ttu-id="5852a-112">Valores</span><span class="sxs-lookup"><span data-stu-id="5852a-112">Values</span></span> |
| - | - | - |
| <span data-ttu-id="5852a-113">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="5852a-113">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="5852a-114">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-114">`false` - disabled</span></span><br/><span data-ttu-id="5852a-115">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-115">`true` - enabled</span></span> |
| <span data-ttu-id="5852a-116">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5852a-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="5852a-117">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-117">`0` - disabled</span></span><br/><span data-ttu-id="5852a-118">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-118">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="5852a-119">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="5852a-119">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="5852a-120">Configura se <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> o usa ou pilhas de protocolo http mais antigas ( <xref:System.Net.Http.WinHttpHandler> no Windows e `CurlHandler` uma classe interna implementada sobre [libcurl](https://curl.haxx.se/libcurl/), no Linux).</span><span class="sxs-lookup"><span data-stu-id="5852a-120">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="5852a-121">Você pode estar usando APIs de rede de alto nível em vez de instanciar diretamente a <xref:System.Net.Http.HttpClientHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="5852a-121">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="5852a-122">Essa configuração também afeta qual pilha de protocolo HTTP é usada por APIs de rede de alto nível, incluindo <xref:System.Net.Http.HttpClient> e [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span><span class="sxs-lookup"><span data-stu-id="5852a-122">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="5852a-123">Se você omitir essa configuração, o <xref:System.Net.Http.HttpClientHandler> usará <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="5852a-123">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="5852a-124">Isso é equivalente a definir o valor como `true` .</span><span class="sxs-lookup"><span data-stu-id="5852a-124">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="5852a-125">Você pode definir essa configuração programaticamente chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="5852a-125">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="5852a-126">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5852a-126">Setting name</span></span> | <span data-ttu-id="5852a-127">Valores</span><span class="sxs-lookup"><span data-stu-id="5852a-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="5852a-128">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="5852a-128">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="5852a-129">`true` – habilita o uso de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="5852a-129">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="5852a-130">`false` – habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux</span><span class="sxs-lookup"><span data-stu-id="5852a-130">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="5852a-131">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5852a-131">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="5852a-132">`1` – habilita o uso de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="5852a-132">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="5852a-133">`0` – habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux</span><span class="sxs-lookup"><span data-stu-id="5852a-133">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="5852a-134">A partir do .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="5852a-134">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>

## <a name="latin1-headers-net-core-31-only"></a><span data-ttu-id="5852a-135">Cabeçalhos latino1 (somente .NET Core 3,1)</span><span class="sxs-lookup"><span data-stu-id="5852a-135">Latin1 headers (.NET Core 3.1 only)</span></span>

- <span data-ttu-id="5852a-136">Essa opção permite relaxar a validação do cabeçalho HTTP, permitindo <xref:System.Net.Http.SocketsHttpHandler> enviar caracteres codificados para ISO-8859-1 (latino-1) nos cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="5852a-136">This switch allows relaxing the HTTP header validation, enabling <xref:System.Net.Http.SocketsHttpHandler> to send ISO-8859-1 (Latin-1) encoded characters in headers.</span></span>

- <span data-ttu-id="5852a-137">Se você omitir essa configuração, uma tentativa de enviar um caractere não-ASCII resultará em <xref:System.Net.Http.HttpRequestException> .</span><span class="sxs-lookup"><span data-stu-id="5852a-137">If you omit this setting, an attempt to send a non-ASCII character will result in <xref:System.Net.Http.HttpRequestException>.</span></span> <span data-ttu-id="5852a-138">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="5852a-138">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5852a-139">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5852a-139">Setting name</span></span> | <span data-ttu-id="5852a-140">Valores</span><span class="sxs-lookup"><span data-stu-id="5852a-140">Values</span></span> |
| - | - | - |
| <span data-ttu-id="5852a-141">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="5852a-141">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | <span data-ttu-id="5852a-142">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-142">`false` - disabled</span></span><br/><span data-ttu-id="5852a-143">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-143">`true` - enabled</span></span> |
| <span data-ttu-id="5852a-144">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5852a-144">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | <span data-ttu-id="5852a-145">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-145">`0` - disabled</span></span><br/><span data-ttu-id="5852a-146">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="5852a-146">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="5852a-147">Essa opção só está disponível no .NET Core 3,1 desde a versão 3.1.9, e não nas versões anteriores ou posteriores.</span><span class="sxs-lookup"><span data-stu-id="5852a-147">This option is only available in .NET Core 3.1 since version 3.1.9, and not in previous or later versions.</span></span> <span data-ttu-id="5852a-148">No .NET 5, recomendamos o uso do <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> .</span><span class="sxs-lookup"><span data-stu-id="5852a-148">In .NET 5 we recommend using <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector>.</span></span>
