---
title: "Método CloseEnum"
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
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89f5b7069af0bfdfd732ed1ab4935771a565a20f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="9c6df-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="9c6df-102">CloseEnum Method</span></span>
<span data-ttu-id="9c6df-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="9c6df-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c6df-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c6df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c6df-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9c6df-106">Identificador de enumeração a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="9c6df-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c6df-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9c6df-107">Return Value</span></span>  
 <span data-ttu-id="9c6df-108">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="9c6df-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c6df-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c6df-109">Requirements</span></span>  
 <span data-ttu-id="9c6df-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="9c6df-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6df-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c6df-111">See Also</span></span>  
 [<span data-ttu-id="9c6df-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9c6df-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9c6df-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9c6df-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9c6df-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9c6df-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
