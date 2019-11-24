---
title: Método GetResolutionScope
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: f2b78b35db6306c82e389955c4824875bcf25334
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447230"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="db812-102">Método GetResolutionScope</span><span class="sxs-lookup"><span data-stu-id="db812-102">GetResolutionScope Method</span></span>
<span data-ttu-id="db812-103">Retrieves the scope of a given type.</span><span class="sxs-lookup"><span data-stu-id="db812-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db812-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db812-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="db812-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db812-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="db812-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="db812-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="db812-107">File that is in need of a reference.</span><span class="sxs-lookup"><span data-stu-id="db812-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="db812-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="db812-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="db812-109">Receives the assembly or module reference.</span><span class="sxs-lookup"><span data-stu-id="db812-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db812-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="db812-110">Return Value</span></span>  
 <span data-ttu-id="db812-111">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="db812-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db812-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db812-112">Requirements</span></span>  
 <span data-ttu-id="db812-113">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="db812-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db812-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db812-114">See also</span></span>

- [<span data-ttu-id="db812-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="db812-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="db812-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="db812-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="db812-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="db812-117">ALink API</span></span>](index.md)
