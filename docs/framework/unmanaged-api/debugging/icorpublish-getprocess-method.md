---
title: Método ICorPublish::GetProcess
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b2dcdaed34044122dd2a61c9e0b5bb02f8cc0d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774279"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="454c5-102">Método ICorPublish::GetProcess</span><span class="sxs-lookup"><span data-stu-id="454c5-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="454c5-103">Obtém uma [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instância que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="454c5-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="454c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="454c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="454c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="454c5-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="454c5-106">[in] O identificador do processo.</span><span class="sxs-lookup"><span data-stu-id="454c5-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="454c5-107">[out] Um ponteiro para o endereço de um `ICorPublishProcess` instância que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="454c5-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="454c5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="454c5-108">Remarks</span></span>  
 <span data-ttu-id="454c5-109">`GetProcess` falhará se o processo não existe ou não é um processo gerenciado que pode ser depurado com o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="454c5-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="454c5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="454c5-110">Requirements</span></span>  
 <span data-ttu-id="454c5-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="454c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="454c5-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="454c5-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="454c5-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="454c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="454c5-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="454c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454c5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="454c5-115">See also</span></span>

- [<span data-ttu-id="454c5-116">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="454c5-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
