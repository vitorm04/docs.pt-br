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
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441962"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="a0e86-102">Método INotifySource2::SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="a0e86-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="a0e86-103">Atribui um filtro de notificação para uso com esta origem.</span><span class="sxs-lookup"><span data-stu-id="a0e86-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0e86-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0e86-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0e86-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="a0e86-106">no Uma combinação de bits bit a [NOTIFY_FILTER](notify-filter-enumeration.md) valores de enumeração que identificam retornos de chamada para a API do depurador.</span><span class="sxs-lookup"><span data-stu-id="a0e86-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="a0e86-107">no Um ponteiro para uma estrutura de [USER_THREAD](user-thread-structure.md) que identifica threads para a API do depurador.</span><span class="sxs-lookup"><span data-stu-id="a0e86-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0e86-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a0e86-108">Return Value</span></span>  
 <span data-ttu-id="a0e86-109">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="a0e86-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e86-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0e86-110">Requirements</span></span>  
 <span data-ttu-id="a0e86-111">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="a0e86-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e86-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="a0e86-112">See also</span></span>

- [<span data-ttu-id="a0e86-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="a0e86-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="a0e86-114">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="a0e86-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="a0e86-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="a0e86-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
