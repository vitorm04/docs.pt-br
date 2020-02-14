---
title: Método MemoryStream. InternalGetOriginAndLength (System.IO)
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d82b5080e9fbd5fc6603f1cddae996c75a06d3a3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215470"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="2f1e9-102">Método MemoryStream. InternalGetOriginAndLength</span><span class="sxs-lookup"><span data-stu-id="2f1e9-102">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="2f1e9-103">Obtém os valores internos de origem e o comprimento do fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-103">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="2f1e9-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f1e9-104">Parameters</span></span>

- <span data-ttu-id="2f1e9-105">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="2f1e9-105">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="2f1e9-106">Quando esse método retorna, o deslocamento da matriz de bytes especificado ao criar um novo objeto de <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-106">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="2f1e9-107">Contém 0 se a matriz de bytes foi criada por <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-107">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="2f1e9-108">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="2f1e9-108">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="2f1e9-109">Quando esse método retorna, o número de bytes dentro do fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-109">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f1e9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f1e9-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2f1e9-111">O método `MemoryStream.InternalGetOriginAndLength` é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-111">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2f1e9-112">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f1e9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f1e9-113">Requirements</span></span>

<span data-ttu-id="2f1e9-114">**Namespace:** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="2f1e9-114">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="2f1e9-115">**Assembly:** mscorlib. dll (em mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="2f1e9-115">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="2f1e9-116">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="2f1e9-116">**.NET Framework versions:** Available since 2.0.</span></span>
