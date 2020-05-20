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
ms.openlocfilehash: ff1dabcfc366607639cd98be4392f8dd59dc83a1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442001"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="e91c0-102">Método INotifySink2::OnSyncCallReturn</span><span class="sxs-lookup"><span data-stu-id="e91c0-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="e91c0-103">É invocado quando uma chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="e91c0-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e91c0-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e91c0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e91c0-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="e91c0-106">no ID da chamada de que está sendo retornada.</span><span class="sxs-lookup"><span data-stu-id="e91c0-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="e91c0-107">Consulte [estrutura de CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="e91c0-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="e91c0-108">no Buffer de chamadas.</span><span class="sxs-lookup"><span data-stu-id="e91c0-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="e91c0-109">no Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="e91c0-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e91c0-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e91c0-110">Return Value</span></span>  
 <span data-ttu-id="e91c0-111">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="e91c0-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91c0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e91c0-112">Requirements</span></span>  
 <span data-ttu-id="e91c0-113">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="e91c0-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91c0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e91c0-114">See also</span></span>

- [<span data-ttu-id="e91c0-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="e91c0-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="e91c0-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="e91c0-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="e91c0-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="e91c0-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
