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
ms.openlocfilehash: 021068caa8f1ad2c64e5ca3d18ea25dc827563a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084940"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="5f121-102">Método ICorPublish::GetProcess</span><span class="sxs-lookup"><span data-stu-id="5f121-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="5f121-103">Obtém uma [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instância que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="5f121-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f121-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f121-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f121-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f121-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="5f121-106">[in] O identificador do processo.</span><span class="sxs-lookup"><span data-stu-id="5f121-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="5f121-107">[out] Um ponteiro para o endereço de um `ICorPublishProcess` instância que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="5f121-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f121-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f121-108">Remarks</span></span>  
 <span data-ttu-id="5f121-109">`GetProcess` falhará se o processo não existe ou não é um processo gerenciado que pode ser depurado com o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="5f121-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f121-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f121-110">Requirements</span></span>  
 <span data-ttu-id="5f121-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f121-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f121-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5f121-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5f121-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f121-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f121-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f121-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f121-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f121-115">See also</span></span>

- [<span data-ttu-id="5f121-116">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="5f121-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
