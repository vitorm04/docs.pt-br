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
ms.openlocfilehash: 46f047dbec7ff008873540806b76ffe7085086b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178428"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="8d84c-102">Método ICorPublish::GetProcess</span><span class="sxs-lookup"><span data-stu-id="8d84c-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="8d84c-103">Obtém uma ocorrência [de ICorPublishProcess](icorpublishprocess-interface.md) que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="8d84c-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d84c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d84c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d84c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d84c-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="8d84c-106">[em] O identificador do processo.</span><span class="sxs-lookup"><span data-stu-id="8d84c-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="8d84c-107">[fora] Um ponteiro para o `ICorPublishProcess` endereço de uma instância que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="8d84c-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d84c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d84c-108">Remarks</span></span>  
 <span data-ttu-id="8d84c-109">`GetProcess`falha se o processo não existir ou não for um processo gerenciado que pode ser depurado pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="8d84c-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d84c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d84c-110">Requirements</span></span>  
 <span data-ttu-id="8d84c-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d84c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d84c-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="8d84c-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8d84c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d84c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d84c-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d84c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d84c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d84c-115">See also</span></span>

- [<span data-ttu-id="8d84c-116">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="8d84c-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
