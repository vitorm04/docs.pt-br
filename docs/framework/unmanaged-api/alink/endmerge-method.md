---
title: "Método EndMerge"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58e9cecae43fb69f1ce2e90eb9d6551d287ca7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endmerge-method"></a><span data-ttu-id="2b5f8-102">Método EndMerge</span><span class="sxs-lookup"><span data-stu-id="2b5f8-102">EndMerge Method</span></span>
<span data-ttu-id="2b5f8-103">Indica que todos os atributos personalizados foram mesclados para o escopo de emitir.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b5f8-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b5f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b5f8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2b5f8-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b5f8-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2b5f8-107">Return Value</span></span>  
 <span data-ttu-id="2b5f8-108">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b5f8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b5f8-109">Requirements</span></span>  
 <span data-ttu-id="2b5f8-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="2b5f8-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5f8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b5f8-111">See Also</span></span>  
 [<span data-ttu-id="2b5f8-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="2b5f8-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2b5f8-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="2b5f8-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2b5f8-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="2b5f8-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
