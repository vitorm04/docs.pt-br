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
ms.openlocfilehash: 009f7d20dfd6efc279b3187af8f5c95132ae51e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525229"
---
# <a name="closeenum-method"></a><span data-ttu-id="dac3b-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="dac3b-102">CloseEnum Method</span></span>
<span data-ttu-id="dac3b-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="dac3b-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dac3b-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dac3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dac3b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="dac3b-106">Identificador de enumeração a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="dac3b-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dac3b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dac3b-107">Return Value</span></span>  
 <span data-ttu-id="dac3b-108">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="dac3b-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac3b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dac3b-109">Requirements</span></span>  
 <span data-ttu-id="dac3b-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="dac3b-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac3b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dac3b-111">See also</span></span>
- [<span data-ttu-id="dac3b-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="dac3b-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="dac3b-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="dac3b-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="dac3b-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="dac3b-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
