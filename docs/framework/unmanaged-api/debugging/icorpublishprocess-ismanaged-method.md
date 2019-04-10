---
title: Método ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218284"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="7674f-102">Método ICorPublishProcess::IsManaged</span><span class="sxs-lookup"><span data-stu-id="7674f-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="7674f-103">Obtém um valor que indica se o processo é referenciada por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) é conhecido por ter o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7674f-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7674f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7674f-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7674f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7674f-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="7674f-106">[out] Um ponteiro para um valor booliano que indica se o processo tem código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7674f-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="7674f-107">O valor será `true` se o processo tem gerenciado código; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="7674f-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7674f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7674f-108">Remarks</span></span>  
 <span data-ttu-id="7674f-109">Desde a versão atual do `ICorPublishProcess` permite acesso somente aos processos que têm código gerenciado, `IsManaged` sempre retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="7674f-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7674f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7674f-110">Requirements</span></span>  
 <span data-ttu-id="7674f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7674f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7674f-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7674f-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7674f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7674f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7674f-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7674f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7674f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7674f-115">See also</span></span>

- [<span data-ttu-id="7674f-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="7674f-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
