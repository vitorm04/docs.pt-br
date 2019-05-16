---
title: Método ICorDebugProcess4::ProcessStateChanged
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
ms.openlocfilehash: 5e3a6714489e2051a09b5855ab9f911ef2f57450
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632292"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="ed535-102">Método ICorDebugProcess4::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="ed535-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="ed535-103">Notifica o pipeline ICorDebug que fora do depurador de processo está continuando a execução do depurado.</span><span class="sxs-lookup"><span data-stu-id="ed535-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed535-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed535-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="ed535-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed535-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="ed535-106">[in] Um membro do [enumeração CorDebugStateChange](cordebugstatechange-enumeration.md) que descreve uma alteração no estado de execução do processo.</span><span class="sxs-lookup"><span data-stu-id="ed535-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed535-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed535-107">Remarks</span></span>

<span data-ttu-id="ed535-108">O método fornecido é parte do `ICorDebugProcess4` de interface e corresponde ao slot de quarto da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="ed535-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed535-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed535-109">Requirements</span></span>

 <span data-ttu-id="ed535-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed535-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="ed535-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ed535-111">**Header:** None</span></span>

 <span data-ttu-id="ed535-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ed535-112">**Library:** None</span></span>
 
 <span data-ttu-id="ed535-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed535-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ed535-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed535-114">See also</span></span>

- [<span data-ttu-id="ed535-115">Interface ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="ed535-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="ed535-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ed535-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ed535-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="ed535-117">Debugging</span></span>](index.md)
