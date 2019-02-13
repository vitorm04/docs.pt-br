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
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221128"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="dfa66-102">Enumeração CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="dfa66-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="dfa66-103">Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.</span><span class="sxs-lookup"><span data-stu-id="dfa66-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfa66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfa66-104">Syntax</span></span>

```
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="dfa66-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dfa66-105">Members</span></span>

| <span data-ttu-id="dfa66-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dfa66-106">Member</span></span>            | <span data-ttu-id="dfa66-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfa66-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="dfa66-108">O processo atingiu um novo estado de memória por meio da execução do encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="dfa66-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="dfa66-109">A memória do processo pode ser arbitrariamente diferente do que era anteriormente.</span><span class="sxs-lookup"><span data-stu-id="dfa66-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="dfa66-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfa66-110">Remarks</span></span>

 <span data-ttu-id="dfa66-111">Um membro do `CorDebugStateChange` enumeração é fornecida como um argumento quando o depurador chama o `ProcessStateChanged` método com [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="dfa66-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="dfa66-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfa66-112">Requirements</span></span>

 <span data-ttu-id="dfa66-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa66-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="dfa66-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfa66-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="dfa66-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa66-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="dfa66-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa66-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa66-117">See also</span></span>

- [<span data-ttu-id="dfa66-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="dfa66-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="dfa66-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="dfa66-119">Debugging</span></span>](index.md)
