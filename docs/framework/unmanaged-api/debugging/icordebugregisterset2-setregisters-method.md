---
title: Método ICorDebugRegisterSet2::SetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4cd4f7e1b0737672f33bdd7fec4f7953e20593f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108336"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="244b1-102">Método ICorDebugRegisterSet2::SetRegisters</span><span class="sxs-lookup"><span data-stu-id="244b1-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
`SetRegisters` <span data-ttu-id="244b1-103">não é implementada no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="244b1-103">is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="244b1-104">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="244b1-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="244b1-105">Use as operações de nível mais altos, como [icordebugilframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou [icordebugnativeframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="244b1-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="244b1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="244b1-106">Syntax</span></span>  
  
```  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="244b1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="244b1-107">Requirements</span></span>  
 <span data-ttu-id="244b1-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="244b1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="244b1-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="244b1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="244b1-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="244b1-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="244b1-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="244b1-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="244b1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="244b1-112">See also</span></span>

- [<span data-ttu-id="244b1-113">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="244b1-113">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="244b1-114">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="244b1-114">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
