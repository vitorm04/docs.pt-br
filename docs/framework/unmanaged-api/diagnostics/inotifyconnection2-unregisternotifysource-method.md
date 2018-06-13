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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4b4f90f918c872f3227ac22f4cccadcbf3194a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425474"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="2cb1e-102">Método INotifyConnection2::UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="2cb1e-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="2cb1e-103">Remove um objeto de fonte de notificação especificado a conexão.</span><span class="sxs-lookup"><span data-stu-id="2cb1e-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cb1e-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cb1e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cb1e-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="2cb1e-106">[in] Objeto de notificação a ser cancelado.</span><span class="sxs-lookup"><span data-stu-id="2cb1e-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cb1e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2cb1e-107">Return Value</span></span>  
 <span data-ttu-id="2cb1e-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="2cb1e-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb1e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cb1e-109">Requirements</span></span>  
 <span data-ttu-id="2cb1e-110">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="2cb1e-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb1e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cb1e-111">See Also</span></span>  
 [<span data-ttu-id="2cb1e-112">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="2cb1e-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="2cb1e-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="2cb1e-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="2cb1e-114">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="2cb1e-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="2cb1e-115">Método RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="2cb1e-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
