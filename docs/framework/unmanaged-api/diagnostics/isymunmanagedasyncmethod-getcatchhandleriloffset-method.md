---
title: "Método ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96040ee5f56ade3647367c4b879c8aa9e7f460fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="320cb-102">Método ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="320cb-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="320cb-103">Consulte [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="320cb-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="320cb-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="320cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="320cb-105">Parameters</span></span>  
  
|<span data-ttu-id="320cb-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="320cb-106">Parameter</span></span>|<span data-ttu-id="320cb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="320cb-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="320cb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="320cb-108">Return Value</span></span>  
 <span data-ttu-id="320cb-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="320cb-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320cb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="320cb-110">Requirements</span></span>  
 <span data-ttu-id="320cb-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="320cb-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320cb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="320cb-112">See Also</span></span>  
 [<span data-ttu-id="320cb-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="320cb-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
