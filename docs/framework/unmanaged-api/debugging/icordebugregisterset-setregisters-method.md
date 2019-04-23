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
ms.openlocfilehash: d17c353d8e2358a1651ba3fbbb1dd718cc681f7b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123781"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="598a7-102">Método ICorDebugRegisterSet::SetRegisters</span><span class="sxs-lookup"><span data-stu-id="598a7-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="598a7-103">`SetRegisters` não é implementada no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="598a7-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="598a7-104">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="598a7-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="598a7-105">Use as operações de nível mais altos, como [icordebugilframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou [icordebugnativeframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="598a7-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="598a7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="598a7-106">Syntax</span></span>  
  
```  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="598a7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="598a7-107">Requirements</span></span>  
 <span data-ttu-id="598a7-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="598a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="598a7-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="598a7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="598a7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="598a7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="598a7-111">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="598a7-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="598a7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="598a7-112">See also</span></span>

- [<span data-ttu-id="598a7-113">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="598a7-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="598a7-114">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="598a7-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
