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
ms.openlocfilehash: 85f00698f42f120b209cca14f293a58ae4c65f6f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442027"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="34152-102">Método INotifySink2::OnSyncCallEnter</span><span class="sxs-lookup"><span data-stu-id="34152-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="34152-103">É invocado ao inserir uma chamada.</span><span class="sxs-lookup"><span data-stu-id="34152-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34152-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34152-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34152-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34152-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="34152-106">no ID da chamada que está sendo inserida.</span><span class="sxs-lookup"><span data-stu-id="34152-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="34152-107">Consulte [estrutura de CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="34152-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="34152-108">no Buffer de chamadas.</span><span class="sxs-lookup"><span data-stu-id="34152-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="34152-109">no Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="34152-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34152-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="34152-110">Return Value</span></span>  
 <span data-ttu-id="34152-111">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="34152-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34152-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34152-112">Requirements</span></span>  
 <span data-ttu-id="34152-113">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="34152-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34152-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="34152-114">See also</span></span>

- [<span data-ttu-id="34152-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="34152-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="34152-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="34152-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="34152-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="34152-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
