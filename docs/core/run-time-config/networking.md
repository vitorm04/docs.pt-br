---
title: Configurações de configuração de rede
description: Saiba mais sobre as configurações de tempo de execução que configuram a rede para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802767"
---
# <a name="run-time-configuration-options-for-networking"></a>Opções de configuração em tempo de execução para rede

## <a name="http2-protocol"></a>Protocolo HTTP/2

- Configura se o suporte para o protocolo HTTP/2 está ativado.
- Padrão: Desabilitado ( ).`false`
- Introduzido no .NET Core 3.0.

| | Nome da configuração | Valores |
| - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- deficientes<br/>`true`- habilitado |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- deficientes<br/>`1`- habilitado |

## <a name="sockets-http-handler"></a>Soquetes HTTP manipulador

- Configura se apis de rede de <xref:System.Net.Http.HttpClient>alto <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nível, como <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> , uso ou a implementação do que é baseado em [libcurl](https://curl.haxx.se/libcurl/).
- Padrão: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Uso`true`( ).
- Você pode configurar esta configuração programática, chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- permite o uso de<xref:System.Net.Http.HttpClientHandler> |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- permite o uso de<xref:System.Net.Http.HttpClientHandler> |
