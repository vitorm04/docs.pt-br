---
title: Definições de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6b5e03b127f95911b712b66c0be8a4f5a2929fc2
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761935"
---
# <a name="run-time-configuration-options-for-networking"></a>Opções de configuração de tempo de execução para rede

## <a name="http2-protocol"></a>Protocolo HTTP/2

- Configura se o suporte para o protocolo HTTP/2 está habilitado.

- Se você omitir essa configuração, o suporte para o protocolo HTTP/2 será desabilitado. Isso é equivalente a definir o valor como `false` .

- Introduzido no .NET Core 3,0.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-desabilitado<br/>`true`-habilitado |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-desabilitado<br/>`1`-habilitado |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Configura se <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> o usa ou pilhas de protocolo http mais antigas ( <xref:System.Net.Http.WinHttpHandler> no Windows e `CurlHandler` uma classe interna implementada sobre [libcurl](https://curl.haxx.se/libcurl/), no Linux).

  > [!NOTE]
  > Você pode estar usando APIs de rede de alto nível em vez de instanciar diretamente a <xref:System.Net.Http.HttpClientHandler> classe. Essa configuração também afeta qual pilha de protocolo HTTP é usada por APIs de rede de alto nível, incluindo <xref:System.Net.Http.HttpClient> e [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Se você omitir essa configuração, o <xref:System.Net.Http.HttpClientHandler> usará <xref:System.Net.Http.SocketsHttpHandler> . Isso é equivalente a definir o valor como `true` .

- Você pode definir essa configuração programaticamente chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true`– habilita o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`– habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`– habilita o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`– habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux |

> [!NOTE]
> A partir do .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.
