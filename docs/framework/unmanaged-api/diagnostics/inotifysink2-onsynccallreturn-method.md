---
title: Método INotifySink2::OnSyncCallReturn
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc182687b12f5941996c17f4c09da44c49ef815c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694900"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="b93a3-102">Método INotifySink2::OnSyncCallReturn</span><span class="sxs-lookup"><span data-stu-id="b93a3-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="b93a3-103">É invocado quando uma chamada é retornada.</span><span class="sxs-lookup"><span data-stu-id="b93a3-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b93a3-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b93a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b93a3-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="b93a3-106">[in] ID da chamada seja retornada do.</span><span class="sxs-lookup"><span data-stu-id="b93a3-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="b93a3-107">Ver [estrutura CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b93a3-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="b93a3-108">[in] Buffer de chamada.</span><span class="sxs-lookup"><span data-stu-id="b93a3-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="b93a3-109">[in] Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="b93a3-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b93a3-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b93a3-110">Return Value</span></span>  
 <span data-ttu-id="b93a3-111">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b93a3-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93a3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b93a3-112">Requirements</span></span>  
 <span data-ttu-id="b93a3-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b93a3-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93a3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b93a3-114">See also</span></span>
- [<span data-ttu-id="b93a3-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="b93a3-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="b93a3-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="b93a3-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="b93a3-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="b93a3-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
