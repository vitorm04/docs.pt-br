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
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="9ddaa-102">Propriedade PooledStream. NetworkStream</span><span class="sxs-lookup"><span data-stu-id="9ddaa-102">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="9ddaa-103">Obtém ou define o fluxo de rede para o soquete de `PooledStream`.</span><span class="sxs-lookup"><span data-stu-id="9ddaa-103">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ddaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ddaa-104">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="9ddaa-105">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="9ddaa-105">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="9ddaa-106">O fluxo de rede para o soquete de `PooledStream`.</span><span class="sxs-lookup"><span data-stu-id="9ddaa-106">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ddaa-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ddaa-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9ddaa-108">A propriedade `PooledStream.NetworkStream` é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="9ddaa-108">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9ddaa-109">A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="9ddaa-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ddaa-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ddaa-110">Requirements</span></span>

<span data-ttu-id="9ddaa-111">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9ddaa-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9ddaa-112">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="9ddaa-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="9ddaa-113">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="9ddaa-113">**.NET Framework versions:** Available since 2.0.</span></span>
