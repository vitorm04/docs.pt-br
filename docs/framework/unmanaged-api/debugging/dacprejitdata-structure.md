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
ms.openlocfilehash: 46031f29da6916eeaeea863ebef6924a720d7155
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793822"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="50f01-102">Estrutura DacpReJitData</span><span class="sxs-lookup"><span data-stu-id="50f01-102">DacpReJitData Structure</span></span>

<span data-ttu-id="50f01-103">Define as informações básicas sobre um determinado método de instrumento do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="50f01-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="50f01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50f01-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="50f01-105">Membros</span><span class="sxs-lookup"><span data-stu-id="50f01-105">Members</span></span>

| <span data-ttu-id="50f01-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="50f01-106">Member</span></span>           | <span data-ttu-id="50f01-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="50f01-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="50f01-108">O número de revisão de ReJit para um método.</span><span class="sxs-lookup"><span data-stu-id="50f01-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="50f01-109">Um sinalizador que indica o estado atual da instrumentação ReJit do método para a versão fornecida.</span><span class="sxs-lookup"><span data-stu-id="50f01-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="50f01-110">O endereço base da implementação de rejitted do método.</span><span class="sxs-lookup"><span data-stu-id="50f01-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="50f01-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="50f01-111">Remarks</span></span>

<span data-ttu-id="50f01-112">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="50f01-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="50f01-113">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="50f01-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="50f01-114">A estrutura também deve ser definida usando `ms_struct` empacotamento se não estiver usando os compiladores da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50f01-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="50f01-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="50f01-115">Requirements</span></span>
<span data-ttu-id="50f01-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50f01-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="50f01-117">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="50f01-117">**Header:** None</span></span>  
<span data-ttu-id="50f01-118">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="50f01-118">**Library:** None</span></span>  
<span data-ttu-id="50f01-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50f01-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="50f01-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="50f01-120">See also</span></span>

- [<span data-ttu-id="50f01-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="50f01-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="50f01-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="50f01-122">Debugging Structures</span></span>](debugging-structures.md)
