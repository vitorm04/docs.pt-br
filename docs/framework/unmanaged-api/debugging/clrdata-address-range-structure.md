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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961299"
---
# <a name="clrdataaddressrange-structure"></a><span data-ttu-id="90777-102">Estrutura CLRDATA_ADDRESS_RANGE</span><span class="sxs-lookup"><span data-stu-id="90777-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="90777-103">Define um intervalo de endereços.</span><span class="sxs-lookup"><span data-stu-id="90777-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="90777-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90777-104">Syntax</span></span>

```
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="90777-105">Membros</span><span class="sxs-lookup"><span data-stu-id="90777-105">Members</span></span>

| <span data-ttu-id="90777-106">Membro</span><span class="sxs-lookup"><span data-stu-id="90777-106">Member</span></span>         | <span data-ttu-id="90777-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="90777-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="90777-108">O endereço inicial do intervalo.</span><span class="sxs-lookup"><span data-stu-id="90777-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="90777-109">O endereço final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="90777-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="90777-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="90777-110">Remarks</span></span>

<span data-ttu-id="90777-111">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="90777-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="90777-112">Para usá-lo, definir a estrutura conforme especificado acima, onde `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="90777-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="90777-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90777-113">Requirements</span></span>

<span data-ttu-id="90777-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90777-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="90777-115">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="90777-115">**Header:** None</span></span>  
<span data-ttu-id="90777-116">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="90777-116">**Library:** None</span></span>  
<span data-ttu-id="90777-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="90777-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="90777-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90777-118">See also</span></span>

- [<span data-ttu-id="90777-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="90777-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="90777-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="90777-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
