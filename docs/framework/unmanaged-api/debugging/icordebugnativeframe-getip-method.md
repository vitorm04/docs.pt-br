---
title: Método ICorDebugNativeFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e9149bafc866f89253c4318ac69f2705431e48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765309"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="37299-102">Método ICorDebugNativeFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="37299-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="37299-103">Obtém o código nativo de deslocamento local ao qual o ponteiro de instrução está definido atualmente.</span><span class="sxs-lookup"><span data-stu-id="37299-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37299-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37299-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37299-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37299-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="37299-106">[out] Um ponteiro para o local de deslocamento no código nativo.</span><span class="sxs-lookup"><span data-stu-id="37299-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37299-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="37299-107">Remarks</span></span>  
 <span data-ttu-id="37299-108">Se o registro de ativação que é representado por esse "ICorDebugNativeFrame" estiver ativo, o deslocamento é o endereço da próxima instrução a ser executada.</span><span class="sxs-lookup"><span data-stu-id="37299-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="37299-109">Se este registro de ativação não estiver ativo, o deslocamento é o endereço da próxima instrução a ser executado quando o quadro de pilha for reativado.</span><span class="sxs-lookup"><span data-stu-id="37299-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37299-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37299-110">Requirements</span></span>  
 <span data-ttu-id="37299-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37299-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37299-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37299-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37299-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37299-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37299-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37299-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37299-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37299-115">See also</span></span>
