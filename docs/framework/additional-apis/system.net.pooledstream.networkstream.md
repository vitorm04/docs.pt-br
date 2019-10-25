---
title: Propriedade PooledStream. NetworkStream (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847174"
---
# <a name="pooledstreamnetworkstream-property"></a>Propriedade PooledStream. NetworkStream

Obtém ou define o fluxo de rede para o soquete de `PooledStream`.

## <a name="syntax"></a>Sintaxe

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Net.Sockets.NetworkStream>  
O fluxo de rede para o soquete de `PooledStream`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A propriedade `PooledStream.NetworkStream` é interna e não deve ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System. dll)

**.NET Framework versões:** Disponível desde 2,0.
