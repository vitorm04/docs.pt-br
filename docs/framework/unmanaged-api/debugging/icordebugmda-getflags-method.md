---
title: Método ICorDebugMDA::GetFlags
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 4e5939e9e74899a33f28927c4fda09d0a8fb30a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209728"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="204e1-102">Método ICorDebugMDA::GetFlags</span><span class="sxs-lookup"><span data-stu-id="204e1-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="204e1-103">Obtém os sinalizadores associados ao MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="204e1-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="204e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="204e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="204e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="204e1-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="204e1-106">no Uma combinação de bits bit que indica os valores de enumeração [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) que especificam as configurações dos sinalizadores para este MDA.</span><span class="sxs-lookup"><span data-stu-id="204e1-106">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="204e1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="204e1-107">Requirements</span></span>  
 <span data-ttu-id="204e1-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="204e1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="204e1-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="204e1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="204e1-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="204e1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="204e1-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="204e1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="204e1-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="204e1-112">See also</span></span>

- [<span data-ttu-id="204e1-113">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="204e1-113">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="204e1-114">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="204e1-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
