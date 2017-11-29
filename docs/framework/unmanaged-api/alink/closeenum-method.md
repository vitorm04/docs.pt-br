---
title: "Método CloseEnum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CloseEnum
- IALink.CloseEnum
api_location: alink.dll
api_type: COM
f1_keywords: CloseEnum
helpviewer_keywords: CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6ade939969069fb35221d83f8c7e4e380e903a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="735b2-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="735b2-102">CloseEnum Method</span></span>
<span data-ttu-id="735b2-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="735b2-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="735b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="735b2-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="735b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="735b2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="735b2-106">Identificador de enumeração a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="735b2-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="735b2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="735b2-107">Return Value</span></span>  
 <span data-ttu-id="735b2-108">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="735b2-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="735b2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="735b2-109">Requirements</span></span>  
 <span data-ttu-id="735b2-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="735b2-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="735b2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="735b2-111">See Also</span></span>  
 [<span data-ttu-id="735b2-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="735b2-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="735b2-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="735b2-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="735b2-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="735b2-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
