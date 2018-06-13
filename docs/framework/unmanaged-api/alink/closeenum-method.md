---
title: Método CloseEnum
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5c3185dc6d488223d5882f543f0c690d82261b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402438"
---
# <a name="closeenum-method"></a><span data-ttu-id="c3b69-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="c3b69-102">CloseEnum Method</span></span>
<span data-ttu-id="c3b69-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="c3b69-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3b69-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3b69-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3b69-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c3b69-106">Identificador de enumeração a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="c3b69-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3b69-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c3b69-107">Return Value</span></span>  
 <span data-ttu-id="c3b69-108">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="c3b69-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b69-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3b69-109">Requirements</span></span>  
 <span data-ttu-id="c3b69-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="c3b69-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b69-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3b69-111">See Also</span></span>  
 [<span data-ttu-id="c3b69-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c3b69-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c3b69-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c3b69-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c3b69-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c3b69-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
