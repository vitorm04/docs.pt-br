---
title: Método ICorDebugController::IsRunning
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
ms.openlocfilehash: 89ea9f221ad55063e4186cc27cc8038334d800d4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892874"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="5facd-102">Método ICorDebugController::IsRunning</span><span class="sxs-lookup"><span data-stu-id="5facd-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="5facd-103">Obtém um valor que indica se os threads no processo estão em execução livremente no momento.</span><span class="sxs-lookup"><span data-stu-id="5facd-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5facd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5facd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5facd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5facd-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="5facd-106">fora Um ponteiro para um valor que `true` se os threads no processo estão em execução livremente; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="5facd-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5facd-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5facd-107">Requirements</span></span>  
 <span data-ttu-id="5facd-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5facd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5facd-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5facd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5facd-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5facd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5facd-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5facd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5facd-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="5facd-112">See also</span></span>
