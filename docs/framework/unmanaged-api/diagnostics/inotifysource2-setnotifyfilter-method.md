---
title: Método INotifySource2::SetNotifyFilter
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37e4abeebce155a4c332e864b4dfb6cf5a1141ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940329"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="3097a-102">Método INotifySource2::SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="3097a-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="3097a-103">Atribui um filtro de notificação para uso com essa origem.</span><span class="sxs-lookup"><span data-stu-id="3097a-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3097a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3097a-104">Syntax</span></span>  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3097a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3097a-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="3097a-106">[in] Uma combinação bit a bit do [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) valores de enumeração que identificam os retornos de chamada para a API do depurador.</span><span class="sxs-lookup"><span data-stu-id="3097a-106">[in] A bitwise combination of the [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="3097a-107">[in] Um ponteiro para um [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) estrutura que identifica os threads para a API do depurador.</span><span class="sxs-lookup"><span data-stu-id="3097a-107">[in] A pointer to a [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3097a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3097a-108">Return Value</span></span>  
 <span data-ttu-id="3097a-109">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="3097a-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3097a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3097a-110">Requirements</span></span>  
 <span data-ttu-id="3097a-111">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="3097a-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3097a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3097a-112">See also</span></span>

- [<span data-ttu-id="3097a-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="3097a-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="3097a-114">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="3097a-114">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="3097a-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="3097a-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
