---
title: "Método ICorPublishProcess::IsManaged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21fdb09820acb6357fe1457d2f96c3319b3152a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="c3c4b-102">Método ICorPublishProcess::IsManaged</span><span class="sxs-lookup"><span data-stu-id="c3c4b-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="c3c4b-103">Obtém um valor que indica se o processo é referenciada por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) é conhecido por ter código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3c4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3c4b-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3c4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3c4b-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="c3c4b-106">[out] Um ponteiro para um valor booliano que indica se o processo tem código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="c3c4b-107">O valor é `true` se o processo tem gerenciado código; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3c4b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3c4b-108">Remarks</span></span>  
 <span data-ttu-id="c3c4b-109">Desde a versão atual do `ICorPublishProcess` permite acesso somente aos processos que têm código gerenciado, `IsManaged` sempre retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3c4b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3c4b-110">Requirements</span></span>  
 <span data-ttu-id="c3c4b-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3c4b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3c4b-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c3c4b-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c3c4b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3c4b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3c4b-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3c4b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c4b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3c4b-115">See Also</span></span>  
 [<span data-ttu-id="c3c4b-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="c3c4b-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
