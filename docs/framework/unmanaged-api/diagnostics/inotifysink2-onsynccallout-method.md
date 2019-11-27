---
title: Método INotifySink2::OnSyncCallOut
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: e7b3d5bd53bb9e4d6b897bfbf109c1f7307224cd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442511"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="6fbc9-102">Método INotifySink2::OnSyncCallOut</span><span class="sxs-lookup"><span data-stu-id="6fbc9-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="6fbc9-103">É invocado quando uma chamada está fora.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbc9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fbc9-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fbc9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fbc9-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="6fbc9-106">no ID da chamada que está fora. Consulte [estrutura de CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="6fbc9-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="6fbc9-107">fora Buffer de chamadas.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="6fbc9-108">fora Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fbc9-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6fbc9-109">Return Value</span></span>  
 <span data-ttu-id="6fbc9-110">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fbc9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fbc9-111">Requirements</span></span>  
 <span data-ttu-id="6fbc9-112">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="6fbc9-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbc9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fbc9-113">See also</span></span>

- [<span data-ttu-id="6fbc9-114">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="6fbc9-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="6fbc9-115">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="6fbc9-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="6fbc9-116">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="6fbc9-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
