---
title: Enumeração CorSymVarFlag
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 21e92d8f2fb80c4c41d516ef281bf4fc8a75f4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176637"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="5727d-102">Enumeração CorSymVarFlag</span><span class="sxs-lookup"><span data-stu-id="5727d-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="5727d-103">Indica se uma variável é gerada pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="5727d-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5727d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5727d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="5727d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5727d-105">Members</span></span>  
  
|<span data-ttu-id="5727d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5727d-106">Member</span></span>|<span data-ttu-id="5727d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5727d-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="5727d-108">Indica que a variável dada é gerada pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="5727d-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5727d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5727d-109">Requirements</span></span>  
 <span data-ttu-id="5727d-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5727d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5727d-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="5727d-111">See also</span></span>

- [<span data-ttu-id="5727d-112">Enumerações de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5727d-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
