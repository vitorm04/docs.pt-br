---
title: Método ICLRDataTarget::GetCurrentThreadID
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc4ba4f87cd53e12baa0a7cf8b853db0e948201f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500366"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="a75fd-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="a75fd-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="a75fd-103">Obtém o identificador de sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="a75fd-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a75fd-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a75fd-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a75fd-106">[out] Um ponteiro para o identificador de sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="a75fd-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a75fd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a75fd-107">Remarks</span></span>  
 <span data-ttu-id="a75fd-108">Se não houver nenhum thread atual para o processo de destino, o `GetCurrentThreadID` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="a75fd-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75fd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a75fd-109">Requirements</span></span>  
 <span data-ttu-id="a75fd-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75fd-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a75fd-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a75fd-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a75fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a75fd-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a75fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75fd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a75fd-114">See also</span></span>
- [<span data-ttu-id="a75fd-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="a75fd-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
