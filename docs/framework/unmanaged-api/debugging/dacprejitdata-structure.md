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
ms.openlocfilehash: 77ef2c65157df4a033700bb8d0295875ede46554
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739114"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="fbe2f-102">Estrutura DacpReJitData</span><span class="sxs-lookup"><span data-stu-id="fbe2f-102">DacpReJitData Structure</span></span>

<span data-ttu-id="fbe2f-103">Define as informações básicas sobre um determinado método instrumentados pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fbe2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbe2f-104">Syntax</span></span>

```cpp
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

## <a name="members"></a><span data-ttu-id="fbe2f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fbe2f-105">Members</span></span>

| <span data-ttu-id="fbe2f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fbe2f-106">Member</span></span>           | <span data-ttu-id="fbe2f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbe2f-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="fbe2f-108">O número de revisão do ReJit para um método.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="fbe2f-109">Um sinalizador que indica o estado atual de instrumentação do ReJit do método para a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="fbe2f-110">O endereço básico da implementação de rejitted do método.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="fbe2f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbe2f-111">Remarks</span></span>

<span data-ttu-id="fbe2f-112">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fbe2f-113">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="fbe2f-114">A estrutura também deve ser definida usando `ms_struct` de remessa se não estiver usando os compiladores Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbe2f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbe2f-115">Requirements</span></span>
<span data-ttu-id="fbe2f-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fbe2f-117">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="fbe2f-117">**Header:** None</span></span>  
<span data-ttu-id="fbe2f-118">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="fbe2f-118">**Library:** None</span></span>  
<span data-ttu-id="fbe2f-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fbe2f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fbe2f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbe2f-120">See also</span></span>

- [<span data-ttu-id="fbe2f-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="fbe2f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="fbe2f-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="fbe2f-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
