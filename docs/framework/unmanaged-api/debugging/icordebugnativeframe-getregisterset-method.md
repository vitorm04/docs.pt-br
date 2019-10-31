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
ms.openlocfilehash: ac7601f89c125cecbfbd212118420a800f495742
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096806"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="ae4d7-102">Método ICorDebugNativeFrame::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="ae4d7-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="ae4d7-103">Obtém o conjunto de registros para este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="ae4d7-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae4d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae4d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae4d7-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="ae4d7-106">fora Um ponteiro para o endereço de um objeto [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) que representa o conjunto de registros para esse quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="ae4d7-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae4d7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae4d7-107">Requirements</span></span>  
 <span data-ttu-id="ae4d7-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae4d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae4d7-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae4d7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae4d7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae4d7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae4d7-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae4d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4d7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae4d7-112">See also</span></span>
