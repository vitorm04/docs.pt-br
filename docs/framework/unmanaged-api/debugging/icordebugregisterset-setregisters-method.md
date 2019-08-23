---
title: Método ICorDebugRegisterSet::SetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200ea1b9c046b8743699a549c07c0baaf285be39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965031"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="5d097-102">Método ICorDebugRegisterSet::SetRegisters</span><span class="sxs-lookup"><span data-stu-id="5d097-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="5d097-103">`SetRegisters`Não está implementado na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="5d097-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5d097-104">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="5d097-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d097-105">Use as operações de nível superior, como [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d097-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d097-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d097-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5d097-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d097-107">Requirements</span></span>  
 <span data-ttu-id="5d097-108">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d097-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d097-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d097-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d097-110">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d097-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d097-111">**.NET Framework versões:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="5d097-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d097-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d097-112">See also</span></span>

- [<span data-ttu-id="5d097-113">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="5d097-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="5d097-114">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="5d097-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
