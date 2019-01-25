---
title: Método ICorDebugNativeFrame::GetRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8714cecb343d21fd119a925d2fc7c23abbaebbe1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664441"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="f1aaa-102">Método ICorDebugNativeFrame::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="f1aaa-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="f1aaa-103">Obtém o conjunto de registros deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="f1aaa-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1aaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1aaa-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1aaa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1aaa-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="f1aaa-106">[out] Um ponteiro para o endereço de um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) objeto que representa o registro definido para este registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="f1aaa-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1aaa-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1aaa-107">Requirements</span></span>  
 <span data-ttu-id="f1aaa-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1aaa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1aaa-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1aaa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1aaa-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1aaa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1aaa-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1aaa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1aaa-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1aaa-112">See also</span></span>

