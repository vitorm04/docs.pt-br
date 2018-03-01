---
title: "Método INotifySink2::OnSyncCallExit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43139e8be9a1f5dfb6513f2ee7768237ae882c69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="93e14-102">Método INotifySink2::OnSyncCallExit</span><span class="sxs-lookup"><span data-stu-id="93e14-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="93e14-103">Chamado quando você sair de uma chamada.</span><span class="sxs-lookup"><span data-stu-id="93e14-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93e14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93e14-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93e14-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93e14-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="93e14-106">[in] ID de chamada que está sendo encerrada.</span><span class="sxs-lookup"><span data-stu-id="93e14-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="93e14-107">Consulte [estrutura CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="93e14-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="93e14-108">[out] Buffer de chamada.</span><span class="sxs-lookup"><span data-stu-id="93e14-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="93e14-109">[out] Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="93e14-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93e14-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="93e14-110">Return Value</span></span>  
 <span data-ttu-id="93e14-111">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="93e14-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93e14-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93e14-112">Requirements</span></span>  
 <span data-ttu-id="93e14-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="93e14-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e14-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93e14-114">See Also</span></span>  
 [<span data-ttu-id="93e14-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="93e14-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="93e14-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="93e14-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="93e14-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="93e14-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
