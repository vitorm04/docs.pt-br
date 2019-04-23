---
title: Estrutura DacpReJitData
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122792"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="533d1-102">Estrutura DacpReJitData</span><span class="sxs-lookup"><span data-stu-id="533d1-102">DacpReJitData Structure</span></span>

<span data-ttu-id="533d1-103">Define as informações básicas sobre um determinado método instrumentados pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="533d1-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="533d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="533d1-104">Syntax</span></span>

```
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="533d1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="533d1-105">Members</span></span>

| <span data-ttu-id="533d1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="533d1-106">Member</span></span>           | <span data-ttu-id="533d1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="533d1-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="533d1-108">O número de revisão do ReJit para um método.</span><span class="sxs-lookup"><span data-stu-id="533d1-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="533d1-109">Um sinalizador que indica o estado atual de instrumentação do ReJit do método para a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="533d1-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="533d1-110">O endereço básico da implementação de rejitted do método.</span><span class="sxs-lookup"><span data-stu-id="533d1-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="533d1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="533d1-111">Remarks</span></span>

<span data-ttu-id="533d1-112">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="533d1-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="533d1-113">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="533d1-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="533d1-114">A estrutura também deve ser definida usando `ms_struct` de remessa se não estiver usando os compiladores Microsoft.</span><span class="sxs-lookup"><span data-stu-id="533d1-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="533d1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="533d1-115">Requirements</span></span>
<span data-ttu-id="533d1-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="533d1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="533d1-117">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="533d1-117">**Header:** None</span></span>  
<span data-ttu-id="533d1-118">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="533d1-118">**Library:** None</span></span>  
<span data-ttu-id="533d1-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="533d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="533d1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="533d1-120">See also</span></span>

- [<span data-ttu-id="533d1-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="533d1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="533d1-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="533d1-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
