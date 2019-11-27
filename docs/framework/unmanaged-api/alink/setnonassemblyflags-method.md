---
title: Método SetNonAssemblyFlags
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
ms.openlocfilehash: 2dcb363a2a84b3c2e0438e45663b96d9a0f83f61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445544"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="41be9-102">Método SetNonAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="41be9-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="41be9-103">Define sinalizadores que não são específicos do assembly.</span><span class="sxs-lookup"><span data-stu-id="41be9-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41be9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41be9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="41be9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41be9-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="41be9-106">Sinalizadores ALink.</span><span class="sxs-lookup"><span data-stu-id="41be9-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41be9-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="41be9-107">Return Value</span></span>  
 <span data-ttu-id="41be9-108">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="41be9-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41be9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41be9-109">Requirements</span></span>  
 <span data-ttu-id="41be9-110">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="41be9-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41be9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41be9-111">See also</span></span>

- [<span data-ttu-id="41be9-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="41be9-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="41be9-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="41be9-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="41be9-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="41be9-114">ALink API</span></span>](index.md)
