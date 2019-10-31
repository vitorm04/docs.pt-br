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
ms.openlocfilehash: 64ed875059730e91e28ff0903ab93fb25c68910b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134108"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="ac5c5-102">Método ICorDebug::GetProcess</span><span class="sxs-lookup"><span data-stu-id="ac5c5-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="ac5c5-103">Obtém um ponteiro para a instância "ICorDebugProcess" para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="ac5c5-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac5c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac5c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac5c5-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="ac5c5-106">no A ID do processo.</span><span class="sxs-lookup"><span data-stu-id="ac5c5-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="ac5c5-107">fora Um ponteiro para o endereço de uma instância de `ICorDebugProcess` para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="ac5c5-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5c5-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac5c5-108">Requirements</span></span>  
 <span data-ttu-id="ac5c5-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac5c5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5c5-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac5c5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac5c5-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac5c5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac5c5-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5c5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5c5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac5c5-113">See also</span></span>

- [<span data-ttu-id="ac5c5-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="ac5c5-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
