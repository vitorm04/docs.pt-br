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
ms.openlocfilehash: 9687f6139d67a2387091367c2c72167e03be4eee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698276"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="bd866-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="bd866-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="bd866-103">Obtém o identificador de sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="bd866-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd866-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd866-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd866-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd866-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="bd866-106">[out] Um ponteiro para o identificador de sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd866-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd866-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd866-107">Remarks</span></span>  
 <span data-ttu-id="bd866-108">Se não houver nenhum thread atual para o processo de destino, o `GetCurrentThreadID` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="bd866-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd866-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd866-109">Requirements</span></span>  
 <span data-ttu-id="bd866-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd866-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd866-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="bd866-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bd866-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd866-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd866-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd866-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd866-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd866-114">See also</span></span>

- [<span data-ttu-id="bd866-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="bd866-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
