---
title: "Método ICLRDataTarget::GetCurrentThreadID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetCurrentThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fd2c39b20b823e18232081d1655a6770bafccc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="03693-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="03693-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="03693-103">Obtém o identificador de sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="03693-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03693-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03693-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03693-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03693-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="03693-106">[out] Um ponteiro para o identificador de sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="03693-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03693-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="03693-107">Remarks</span></span>  
 <span data-ttu-id="03693-108">Se não houver nenhum thread atual para o processo de destino, o `GetCurrentThreadID` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="03693-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03693-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03693-109">Requirements</span></span>  
 <span data-ttu-id="03693-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03693-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03693-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="03693-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="03693-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03693-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03693-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03693-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03693-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03693-114">See Also</span></span>  
 [<span data-ttu-id="03693-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="03693-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
