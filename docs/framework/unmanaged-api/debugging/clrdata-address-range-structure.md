---
title: Estrutura CLRDATA_ADDRESS_RANGE
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 484ca79483fc4a5d8f0d1cf2cd5a961c297249e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654796"
---
# <a name="clrdataaddressrange-structure"></a><span data-ttu-id="bfc37-102">Estrutura CLRDATA_ADDRESS_RANGE</span><span class="sxs-lookup"><span data-stu-id="bfc37-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="bfc37-103">Define um intervalo de endereços.</span><span class="sxs-lookup"><span data-stu-id="bfc37-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bfc37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfc37-104">Syntax</span></span>

```
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="bfc37-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bfc37-105">Members</span></span>

| <span data-ttu-id="bfc37-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bfc37-106">Member</span></span>         | <span data-ttu-id="bfc37-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfc37-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="bfc37-108">O endereço inicial do intervalo.</span><span class="sxs-lookup"><span data-stu-id="bfc37-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="bfc37-109">O endereço final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="bfc37-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="bfc37-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfc37-110">Remarks</span></span>

<span data-ttu-id="bfc37-111">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bfc37-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bfc37-112">Para usá-lo, definir a estrutura conforme especificado acima, onde `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bfc37-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfc37-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfc37-113">Requirements</span></span>

<span data-ttu-id="bfc37-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfc37-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bfc37-115">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="bfc37-115">**Header:** None</span></span>  
<span data-ttu-id="bfc37-116">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="bfc37-116">**Library:** None</span></span>  
<span data-ttu-id="bfc37-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bfc37-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bfc37-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfc37-118">See also</span></span>

- [<span data-ttu-id="bfc37-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="bfc37-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="bfc37-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="bfc37-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
