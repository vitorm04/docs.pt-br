---
title: 'ICorDebugProcess4: método rocessStateChanged de:P'
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213563"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="e2b2b-102">ICorDebugProcess4: método rocessStateChanged de:P</span><span class="sxs-lookup"><span data-stu-id="e2b2b-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="e2b2b-103">Notifica o pipeline ICorDebug que o depurador fora do processo está continuando a execução do depurador.</span><span class="sxs-lookup"><span data-stu-id="e2b2b-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2b2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2b2b-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="e2b2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e2b2b-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="e2b2b-106">no Um membro da [Enumeração CorDebugStateChange](cordebugstatechange-enumeration.md) que descreve uma alteração no estado de execução do processo.</span><span class="sxs-lookup"><span data-stu-id="e2b2b-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2b2b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2b2b-107">Remarks</span></span>

<span data-ttu-id="e2b2b-108">O método fornecido faz parte da `ICorDebugProcess4` interface e corresponde ao quarto slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="e2b2b-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2b2b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e2b2b-109">Requirements</span></span>

 <span data-ttu-id="e2b2b-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2b2b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e2b2b-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="e2b2b-111">**Header:** None</span></span>

 <span data-ttu-id="e2b2b-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="e2b2b-112">**Library:** None</span></span>

 <span data-ttu-id="e2b2b-113">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2b2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e2b2b-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2b2b-114">See also</span></span>

- [<span data-ttu-id="e2b2b-115">Interface ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="e2b2b-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="e2b2b-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e2b2b-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e2b2b-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="e2b2b-117">Debugging</span></span>](index.md)
