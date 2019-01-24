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
ms.openlocfilehash: 5895dc3cb64b72380dead1e048c012b586c4f48e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550715"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="cb07b-102">Método INotifyConnection2::RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="cb07b-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="cb07b-103">Instala uma fonte de notificação especificado.</span><span class="sxs-lookup"><span data-stu-id="cb07b-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb07b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb07b-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb07b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb07b-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="cb07b-106">[in] Especifica o objeto a ser usado como a origem da notificação.</span><span class="sxs-lookup"><span data-stu-id="cb07b-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="cb07b-107">[out] Recebe o objeto a ser usado como o coletor de notificação.</span><span class="sxs-lookup"><span data-stu-id="cb07b-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb07b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cb07b-108">Return Value</span></span>  
 <span data-ttu-id="cb07b-109">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="cb07b-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb07b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb07b-110">Requirements</span></span>  
 <span data-ttu-id="cb07b-111">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="cb07b-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb07b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb07b-112">See also</span></span>
- [<span data-ttu-id="cb07b-113">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="cb07b-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="cb07b-114">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="cb07b-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="cb07b-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="cb07b-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="cb07b-116">Método UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="cb07b-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
