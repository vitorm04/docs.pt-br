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

- Configura se <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> usa ou empilha<xref:System.Net.Http.WinHttpHandler> de protocoloHTTP mais antigo (no Windows e, `CurlHandler`uma classe interna implementada em cima do [libcurl](https://curl.haxx.se/libcurl/), no Linux).

  > [!NOTE]
  > Você pode estar usando APIs de rede de alto <xref:System.Net.Http.HttpClientHandler> nível em vez de instanciar diretamente a classe. Essa configuração também afeta a pilha de protocolos HTTP que <xref:System.Net.Http.HttpClient> é usada por APIs de rede de alto nível, incluindo e [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Padrão: <xref:System.Net.Http.SocketsHttpHandler> Uso`true`( ).

- Você pode configurar esta configuração programática, chamando o <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- permite o <xref:System.Net.Http.WinHttpHandler> uso de no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux |
| **Variável de ambiente** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- permite o uso de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- permite o <xref:System.Net.Http.WinHttpHandler> uso de no Windows ou [libcurl](https://curl.haxx.se/libcurl/) no Linux |

> [!NOTE]
> A partir de .NET 5, a `System.Net.Http.UseSocketsHttpHandler` configuração não está mais disponível.
