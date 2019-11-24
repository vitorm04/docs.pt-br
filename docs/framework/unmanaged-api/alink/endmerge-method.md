---
title: Método EndMerge
ms.date: 03/30/2017
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
ms.openlocfilehash: cacf7eab1e53f590ad46fd98ed2f5dcbd14cd30a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434414"
---
# <a name="endmerge-method"></a><span data-ttu-id="7be0d-102">Método EndMerge</span><span class="sxs-lookup"><span data-stu-id="7be0d-102">EndMerge Method</span></span>
<span data-ttu-id="7be0d-103">Indicates that all custom attributes have been merged into the emit scope.</span><span class="sxs-lookup"><span data-stu-id="7be0d-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7be0d-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7be0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7be0d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7be0d-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="7be0d-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7be0d-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7be0d-107">Return Value</span></span>  
 <span data-ttu-id="7be0d-108">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="7be0d-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be0d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7be0d-109">Requirements</span></span>  
 <span data-ttu-id="7be0d-110">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="7be0d-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be0d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7be0d-111">See also</span></span>

- [<span data-ttu-id="7be0d-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7be0d-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7be0d-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7be0d-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7be0d-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7be0d-114">ALink API</span></span>](index.md)
