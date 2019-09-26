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
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274306"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="d5c6d-102">Estrutura CLRDATA_ADDRESS_RANGE</span><span class="sxs-lookup"><span data-stu-id="d5c6d-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="d5c6d-103">Define um intervalo de endereços.</span><span class="sxs-lookup"><span data-stu-id="d5c6d-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d5c6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5c6d-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="d5c6d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d5c6d-105">Members</span></span>

| <span data-ttu-id="d5c6d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d5c6d-106">Member</span></span>         | <span data-ttu-id="d5c6d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5c6d-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="d5c6d-108">O endereço inicial do intervalo.</span><span class="sxs-lookup"><span data-stu-id="d5c6d-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="d5c6d-109">O endereço final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="d5c6d-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="d5c6d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5c6d-110">Remarks</span></span>

<span data-ttu-id="d5c6d-111">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d5c6d-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d5c6d-112">Para usá-lo, defina a estrutura conforme especificado acima, `CLRDATA_ADDRESS` em que é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d5c6d-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5c6d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5c6d-113">Requirements</span></span>

<span data-ttu-id="d5c6d-114">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c6d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d5c6d-115">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="d5c6d-115">**Header:** None</span></span>  
<span data-ttu-id="d5c6d-116">**Biblioteca** Nenhum</span><span class="sxs-lookup"><span data-stu-id="d5c6d-116">**Library:** None</span></span>  
<span data-ttu-id="d5c6d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c6d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d5c6d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5c6d-118">See also</span></span>

- [<span data-ttu-id="d5c6d-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="d5c6d-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="d5c6d-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="d5c6d-120">Debugging Structures</span></span>](debugging-structures.md)
