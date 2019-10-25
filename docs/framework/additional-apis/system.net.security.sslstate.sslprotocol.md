---
title: Propriedade SslState. SslProtocol (System .net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847195"
---
# <a name="sslstatesslprotocol-property"></a>Propriedade SslState. SslProtocol

Obtém as versões do protocolo SSL.

## <a name="syntax"></a>Sintaxe

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Security.Authentication.SslProtocols>  
Uma combinação de bits de bit que especifica as versões de protocolo SSL.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A propriedade `SslState.SslProtocol` é interna e não deve ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net.Security>

**Assembly:** Sistema (em System. dll)

**.NET Framework versões:** Disponível desde 2,0.
