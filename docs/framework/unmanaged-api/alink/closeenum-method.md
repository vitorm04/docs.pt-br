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
ms.openlocfilehash: 8d9529022eb04c81152dced5c63f255c510851a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777463"
---
# <a name="closeenum-method"></a><span data-ttu-id="7c80a-102">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="7c80a-102">CloseEnum Method</span></span>
<span data-ttu-id="7c80a-103">Fecha a enumeração indicada e libera os recursos associados.</span><span class="sxs-lookup"><span data-stu-id="7c80a-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c80a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c80a-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c80a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c80a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7c80a-106">Identificador da enumeração a ser fechada.</span><span class="sxs-lookup"><span data-stu-id="7c80a-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c80a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7c80a-107">Return Value</span></span>  
 <span data-ttu-id="7c80a-108">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="7c80a-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c80a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c80a-109">Requirements</span></span>  
 <span data-ttu-id="7c80a-110">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="7c80a-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c80a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c80a-111">See also</span></span>

- [<span data-ttu-id="7c80a-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7c80a-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7c80a-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7c80a-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7c80a-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7c80a-114">ALink API</span></span>](index.md)
