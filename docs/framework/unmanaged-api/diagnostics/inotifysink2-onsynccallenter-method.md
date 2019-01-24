---
title: Método INotifySink2::OnSyncCallEnter
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c44a150fa85ff0cbda4ff2b39acefb46045adad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500283"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="30b49-102">Método INotifySink2::OnSyncCallEnter</span><span class="sxs-lookup"><span data-stu-id="30b49-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="30b49-103">É invocado ao inserir uma chamada.</span><span class="sxs-lookup"><span data-stu-id="30b49-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30b49-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30b49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30b49-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="30b49-106">[in] ID da chamada que está sendo inserida.</span><span class="sxs-lookup"><span data-stu-id="30b49-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="30b49-107">Ver [estrutura CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="30b49-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="30b49-108">[in] Buffer de chamada.</span><span class="sxs-lookup"><span data-stu-id="30b49-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="30b49-109">[in] Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="30b49-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30b49-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="30b49-110">Return Value</span></span>  
 <span data-ttu-id="30b49-111">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="30b49-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b49-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30b49-112">Requirements</span></span>  
 <span data-ttu-id="30b49-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="30b49-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b49-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30b49-114">See also</span></span>
- [<span data-ttu-id="30b49-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="30b49-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="30b49-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="30b49-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="30b49-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="30b49-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
