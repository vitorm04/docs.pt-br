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
ms.openlocfilehash: 03ce49466587d3e214c32e2a5cca89cdd7a72038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405221"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="2dd28-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="2dd28-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="2dd28-103">Obtém o identificador de sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="2dd28-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dd28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2dd28-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2dd28-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2dd28-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="2dd28-106">[out] Um ponteiro para o identificador de sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="2dd28-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2dd28-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2dd28-107">Remarks</span></span>  
 <span data-ttu-id="2dd28-108">Se não houver nenhum thread atual para o processo de destino, o `GetCurrentThreadID` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="2dd28-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dd28-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2dd28-109">Requirements</span></span>  
 <span data-ttu-id="2dd28-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dd28-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dd28-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2dd28-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2dd28-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2dd28-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dd28-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dd28-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd28-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2dd28-114">See Also</span></span>  
 [<span data-ttu-id="2dd28-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="2dd28-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
