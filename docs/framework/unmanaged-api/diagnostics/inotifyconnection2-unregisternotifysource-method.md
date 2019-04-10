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
ms.openlocfilehash: 742be1467d2f1e6eb7d8567ddf85f8e65ea4b8d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229453"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="47389-102">Método INotifyConnection2::UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="47389-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="47389-103">Remove um objeto de fonte de notificação especificados a conexão.</span><span class="sxs-lookup"><span data-stu-id="47389-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47389-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47389-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47389-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47389-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="47389-106">[in] Objeto de notificação a ser cancelado.</span><span class="sxs-lookup"><span data-stu-id="47389-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47389-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47389-107">Return Value</span></span>  
 <span data-ttu-id="47389-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="47389-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47389-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47389-109">Requirements</span></span>  
 <span data-ttu-id="47389-110">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="47389-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47389-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47389-111">See also</span></span>

- [<span data-ttu-id="47389-112">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="47389-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="47389-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="47389-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="47389-114">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="47389-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="47389-115">Método RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="47389-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
