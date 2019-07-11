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
ms.openlocfilehash: 45a409bda8861701e68d3ea1a956a4c35ce88ddd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738788"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="bdf07-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="bdf07-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="bdf07-103">Obtém o identificador de sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="bdf07-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdf07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdf07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdf07-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="bdf07-106">[out] Um ponteiro para o identificador de sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bdf07-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdf07-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdf07-107">Remarks</span></span>  
 <span data-ttu-id="bdf07-108">Se não houver nenhum thread atual para o processo de destino, o `GetCurrentThreadID` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="bdf07-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf07-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdf07-109">Requirements</span></span>  
 <span data-ttu-id="bdf07-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf07-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf07-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="bdf07-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bdf07-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf07-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf07-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf07-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf07-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdf07-114">See also</span></span>

- [<span data-ttu-id="bdf07-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="bdf07-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
