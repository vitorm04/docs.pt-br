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
# <a name="run-time-configuration-options-for-networking"></a>Opções de configuração de tempo de execução para rede

## <a name="http2-protocol"></a>Protocolo HTTP/2

- Configura se o suporte para o protocolo HTTP/2 está habilitado.

- Se você omitir essa configuração, o suporte para o protocolo HTTP/2 será desabilitado. Isso é equivalente a definir o valor como `false` .

- Introduzido no .NET Core 3,0.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.jsem** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` -desabilitado<br/>`true` -habilitado |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` -desabilitado<br/>`1` -habilitado |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Configura se <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> o usa ou pilhas de protocolo http mais antigas ( <xref:System.Net.Http.WinHttpHandler> no Windows e `CurlHandler` uma classe interna implementada sobre [libcurl](https://curl.haxx.se/libcurl/), no Linux).

  > [!NOTE]
  > Você pode estar usando APIs de rede de alto nível em vez de instanciar diretamente a <xref:System.Net.Http.HttpClientHandler> classe. Essa configuração também afeta qual pilha de protocolo HTTP é usada por APIs de rede de alto nível, incluindo <xref:System.Net.Http.HttpClient> e [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).

- Se você omitir essa configuração, o <xref:System.Net.Http.HttpClientHandler> usará <xref:System.Net.Http.SocketsHttpHandler> . Isso é equivalente a definir o valor como `true` .

- Você pode definir essa configuração programaticamente chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.jsem** | `System.Net.Http.UseSocketsHttpHandler` | `true` – habilita o uso de <xref:System.Net.Http.SocketsHttpHandler><br/>`false` – habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` – habilita o uso de <xref:System.Net.Http.SocketsHttpHandler><br/>`0` – habilita o uso do <xref:System.Net.Http.WinHttpHandler> no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux |

> [!NOTE]
> A partir do .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.
