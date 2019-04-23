---
title: Método ICorDebugRegisterSet::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f341098268f735a576bdbc5f0cea52f1a7e14f90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156033"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="3739f-102">Método ICorDebugRegisterSet::GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="3739f-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="3739f-103">Obtém um pouco máscara que indica que registra desta [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="3739f-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3739f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3739f-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3739f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3739f-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="3739f-106">[out] Uma máscara de bits que indica quais registros estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="3739f-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3739f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3739f-107">Remarks</span></span>  
 <span data-ttu-id="3739f-108">Um registro pode estar indisponível se seu valor não pode ser determinado para a determinada situação.</span><span class="sxs-lookup"><span data-stu-id="3739f-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="3739f-109">A máscara retornada contém um bit para cada registro (1 << o índice do registro).</span><span class="sxs-lookup"><span data-stu-id="3739f-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="3739f-110">O valor de bit for 1, se o registro estiver disponível, ou 0 se não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="3739f-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3739f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3739f-111">Requirements</span></span>  
 <span data-ttu-id="3739f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3739f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3739f-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3739f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3739f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3739f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3739f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3739f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3739f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3739f-116">See also</span></span>

- [<span data-ttu-id="3739f-117">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="3739f-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="3739f-118">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="3739f-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
