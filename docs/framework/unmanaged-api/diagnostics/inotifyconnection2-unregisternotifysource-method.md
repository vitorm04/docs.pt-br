---
title: Método INotifyConnection2::UnregisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: cf399d0c7dec7528f02988ddfe6ca5c0b1f0c4c3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440992"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="13e92-102">Método INotifyConnection2::UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="13e92-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="13e92-103">Remove um objeto de origem de notificação especificado da conexão.</span><span class="sxs-lookup"><span data-stu-id="13e92-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13e92-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13e92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13e92-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="13e92-106">no Objeto de notificação a ser cancelado.</span><span class="sxs-lookup"><span data-stu-id="13e92-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13e92-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="13e92-107">Return Value</span></span>  
 <span data-ttu-id="13e92-108">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="13e92-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e92-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13e92-109">Requirements</span></span>  
 <span data-ttu-id="13e92-110">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="13e92-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e92-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13e92-111">See also</span></span>

- [<span data-ttu-id="13e92-112">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="13e92-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="13e92-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="13e92-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="13e92-114">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="13e92-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="13e92-115">Método RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="13e92-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
