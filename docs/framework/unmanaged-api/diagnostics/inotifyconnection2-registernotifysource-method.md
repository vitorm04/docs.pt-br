---
title: Método INotifyConnection2::RegisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d3c0d833208c91c548ea993bb6aa32e36e1f358
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776641"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="db3f5-102">Método INotifyConnection2::RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="db3f5-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="db3f5-103">Instala uma fonte de notificação especificado.</span><span class="sxs-lookup"><span data-stu-id="db3f5-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db3f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db3f5-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db3f5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db3f5-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="db3f5-106">[in] Especifica o objeto a ser usado como a origem da notificação.</span><span class="sxs-lookup"><span data-stu-id="db3f5-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="db3f5-107">[out] Recebe o objeto a ser usado como o coletor de notificação.</span><span class="sxs-lookup"><span data-stu-id="db3f5-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db3f5-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db3f5-108">Return Value</span></span>  
 <span data-ttu-id="db3f5-109">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="db3f5-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db3f5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db3f5-110">Requirements</span></span>  
 <span data-ttu-id="db3f5-111">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="db3f5-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3f5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db3f5-112">See also</span></span>

- [<span data-ttu-id="db3f5-113">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="db3f5-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="db3f5-114">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="db3f5-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="db3f5-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="db3f5-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="db3f5-116">Método UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="db3f5-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
