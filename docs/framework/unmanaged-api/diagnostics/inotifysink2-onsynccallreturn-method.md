---
title: "Método INotifySink2::OnSyncCallReturn"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallReturn
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 311f54b5287b648e1c81e4db457e8f3c6945d959
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="6f194-102">Método INotifySink2::OnSyncCallReturn</span><span class="sxs-lookup"><span data-stu-id="6f194-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="6f194-103">Chamado quando uma chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="6f194-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f194-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f194-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f194-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f194-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="6f194-106">[in] ID de chamada que está sendo retornada do.</span><span class="sxs-lookup"><span data-stu-id="6f194-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="6f194-107">Consulte [estrutura CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="6f194-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="6f194-108">[in] Buffer de chamada.</span><span class="sxs-lookup"><span data-stu-id="6f194-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="6f194-109">[in] Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="6f194-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f194-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f194-110">Return Value</span></span>  
 <span data-ttu-id="6f194-111">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="6f194-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f194-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f194-112">Requirements</span></span>  
 <span data-ttu-id="6f194-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6f194-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f194-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f194-114">See Also</span></span>  
 [<span data-ttu-id="6f194-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="6f194-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="6f194-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="6f194-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="6f194-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="6f194-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
