---
title: Enumeração CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739590"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="0c324-102">Enumeração CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="0c324-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="0c324-103">Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.</span><span class="sxs-lookup"><span data-stu-id="0c324-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c324-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c324-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="0c324-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0c324-105">Members</span></span>

| <span data-ttu-id="0c324-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0c324-106">Member</span></span>            | <span data-ttu-id="0c324-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c324-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="0c324-108">O processo atingiu um novo estado de memória por meio da execução do encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="0c324-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="0c324-109">A memória do processo pode ser arbitrariamente diferente do que era anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c324-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="0c324-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c324-110">Remarks</span></span>

 <span data-ttu-id="0c324-111">Um membro do `CorDebugStateChange` enumeração é fornecida como um argumento quando o depurador chama o `ProcessStateChanged` método com [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="0c324-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="0c324-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c324-112">Requirements</span></span>

 <span data-ttu-id="0c324-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c324-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="0c324-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c324-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="0c324-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c324-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="0c324-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c324-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0c324-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c324-117">See also</span></span>

- [<span data-ttu-id="0c324-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="0c324-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="0c324-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="0c324-119">Debugging</span></span>](index.md)
