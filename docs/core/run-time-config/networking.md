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
# <a name="run-time-configuration-options-for-networking"></a>Opções de configuração em tempo de execução para rede

## <a name="http2-protocol"></a>Protocolo HTTP/2

- Configura se o suporte para o protocolo HTTP/2 está ativado.
- Padrão: Desabilitado ( ).`false`
- Introduzido no .NET Core 3.0.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- deficientes<br/>`true`- habilitado |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- deficientes<br/>`1`- habilitado |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Configura se apis de rede de <xref:System.Net.Http.HttpClient>alto <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nível, como <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> , uso ou a implementação do que é baseado em [libcurl](https://curl.haxx.se/libcurl/).
- Padrão: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Uso`true`( ).
- Você pode configurar esta configuração programática, chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- permite o uso de<xref:System.Net.Http.HttpClientHandler> |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- permite o uso de<xref:System.Net.Http.HttpClientHandler> |

> [!NOTE]
> A partir de .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.
