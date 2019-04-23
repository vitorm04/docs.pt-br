---
title: Método ICorDebug::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb869bed71be05e0450580b50dfa9f2a0fca525
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169787"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="4813d-102">Método ICorDebug::GetProcess</span><span class="sxs-lookup"><span data-stu-id="4813d-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="4813d-103">Obtém um ponteiro para a instância de "ICorDebugProcess" para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="4813d-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4813d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4813d-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4813d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4813d-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="4813d-106">[in] A ID do processo.</span><span class="sxs-lookup"><span data-stu-id="4813d-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="4813d-107">[out] Um ponteiro para o endereço de um `ICorDebugProcess` instância para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="4813d-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4813d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4813d-108">Requirements</span></span>  
 <span data-ttu-id="4813d-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4813d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4813d-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4813d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4813d-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4813d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4813d-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4813d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4813d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4813d-113">See also</span></span>

- [<span data-ttu-id="4813d-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="4813d-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
