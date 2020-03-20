---
title: ICorDebugProcess4::ProcessStateChanged Method
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178637"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="af95e-102">ICorDebugProcess4::ProcessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="af95e-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="af95e-103">Notifica o pipeline ICorDebug de que o depurador fora de processo continua a execução do depurador.</span><span class="sxs-lookup"><span data-stu-id="af95e-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="af95e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af95e-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="af95e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="af95e-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="af95e-106">[em] Um membro da [enumeração CorDebugStateChange](cordebugstatechange-enumeration.md) descrevendo uma mudança no estado de execução do processo.</span><span class="sxs-lookup"><span data-stu-id="af95e-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="af95e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="af95e-107">Remarks</span></span>

<span data-ttu-id="af95e-108">O método fornecido faz `ICorDebugProcess4` parte da interface e corresponde ao quarto slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="af95e-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="af95e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af95e-109">Requirements</span></span>

 <span data-ttu-id="af95e-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af95e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="af95e-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="af95e-111">**Header:** None</span></span>

 <span data-ttu-id="af95e-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="af95e-112">**Library:** None</span></span>

 <span data-ttu-id="af95e-113">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af95e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="af95e-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="af95e-114">See also</span></span>

- [<span data-ttu-id="af95e-115">Interface ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="af95e-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="af95e-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="af95e-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="af95e-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="af95e-117">Debugging</span></span>](index.md)
