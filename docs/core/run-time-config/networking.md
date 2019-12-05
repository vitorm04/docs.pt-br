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
# <a name="run-time-configuration-options-for-networking"></a>Opções de configuração de tempo de execução para rede

## <a name="http2-protocol"></a>Protocolo HTTP/2

- Configura se o suporte para o protocolo HTTP/2 está habilitado.
- Padrão: desabilitado (`false`).
- Introduzido no .NET Core 3,0.

| | Nome da configuração | Valores |
| - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-desabilitado<br/>habilitado para `true` |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-desabilitado<br/>habilitado para `1` |

## <a name="sockets-http-handler"></a>Manipulador HTTP de soquetes

- Define se as APIs de rede de alto nível, como <xref:System.Net.Http.HttpClient>, usam <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou a implementação de <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> com base em [libcurl](https://curl.haxx.se/libcurl/).
- Padrão: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).
- Você pode definir essa configuração programaticamente chamando o método <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true`-habilita o uso de <xref:System.Net.Http.SocketsHttpHandler><br/>`false`-habilita o uso de <xref:System.Net.Http.HttpClientHandler> |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`-habilita o uso de <xref:System.Net.Http.SocketsHttpHandler><br/>`0`-habilita o uso de <xref:System.Net.Http.HttpClientHandler> |
