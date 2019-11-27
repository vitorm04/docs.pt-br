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
ms.openlocfilehash: 018af6929ad4023c70bfb975b9be010912415dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446566"
---
# <a name="closeenum-method"></a><span data-ttu-id="b8318-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="b8318-102">CloseEnum Method</span></span>
<span data-ttu-id="b8318-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="b8318-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8318-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8318-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8318-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8318-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b8318-106">Identificador da enumeração a ser fechada.</span><span class="sxs-lookup"><span data-stu-id="b8318-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8318-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b8318-107">Return Value</span></span>  
 <span data-ttu-id="b8318-108">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="b8318-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8318-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b8318-109">Requirements</span></span>  
 <span data-ttu-id="b8318-110">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="b8318-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8318-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8318-111">See also</span></span>

- [<span data-ttu-id="b8318-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="b8318-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b8318-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="b8318-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b8318-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="b8318-114">ALink API</span></span>](index.md)
