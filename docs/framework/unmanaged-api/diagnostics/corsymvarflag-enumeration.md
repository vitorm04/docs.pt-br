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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b387ee7fd4cc0088c90d2b8278fbf18bb36f51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755689"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="882a8-102">Enumeração CorSymVarFlag</span><span class="sxs-lookup"><span data-stu-id="882a8-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="882a8-103">Indica se uma variável é gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="882a8-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="882a8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="882a8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="882a8-105">Members</span></span>  
  
|<span data-ttu-id="882a8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="882a8-106">Member</span></span>|<span data-ttu-id="882a8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="882a8-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="882a8-108">Indica que a variável fornecida é gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="882a8-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="882a8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="882a8-109">Requirements</span></span>  
 <span data-ttu-id="882a8-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="882a8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882a8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="882a8-111">See also</span></span>

- [<span data-ttu-id="882a8-112">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="882a8-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
