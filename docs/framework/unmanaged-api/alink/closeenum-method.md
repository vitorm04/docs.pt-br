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
ms.openlocfilehash: fd7d63596690e2a5d0bc26448884ec09ecd63231
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129513"
---
# <a name="closeenum-method"></a><span data-ttu-id="9cbdd-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="9cbdd-102">CloseEnum Method</span></span>
<span data-ttu-id="9cbdd-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cbdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cbdd-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cbdd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9cbdd-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9cbdd-106">Identificador de enumeração a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cbdd-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9cbdd-107">Return Value</span></span>  
 <span data-ttu-id="9cbdd-108">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cbdd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cbdd-109">Requirements</span></span>  
 <span data-ttu-id="9cbdd-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="9cbdd-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbdd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cbdd-111">See also</span></span>

- [<span data-ttu-id="9cbdd-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9cbdd-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9cbdd-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9cbdd-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9cbdd-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9cbdd-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
