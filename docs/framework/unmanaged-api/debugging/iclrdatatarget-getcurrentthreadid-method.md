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
ms.openlocfilehash: c75c55b64ff20728bc5695d0ddfe1b4f6deda4a6
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860641"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="34671-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="34671-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="34671-103">Obtém o identificador do sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="34671-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34671-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34671-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34671-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34671-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="34671-106">fora Um ponteiro para o identificador do sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="34671-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34671-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="34671-107">Remarks</span></span>  
 <span data-ttu-id="34671-108">Se não houver nenhum thread atual para o processo de destino, `GetCurrentThreadID` o método poderá falhar.</span><span class="sxs-lookup"><span data-stu-id="34671-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34671-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34671-109">Requirements</span></span>  
 <span data-ttu-id="34671-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34671-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34671-111">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="34671-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="34671-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34671-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34671-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34671-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34671-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="34671-114">See also</span></span>

- [<span data-ttu-id="34671-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="34671-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
