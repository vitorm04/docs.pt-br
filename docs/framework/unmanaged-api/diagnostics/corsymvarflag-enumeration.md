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
ms.openlocfilehash: d41e048b67d4bc7159f6dd5266457651f1658290
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420585"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="7fe7a-102">Enumeração CorSymVarFlag</span><span class="sxs-lookup"><span data-stu-id="7fe7a-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="7fe7a-103">Indica se uma variável é gerada pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="7fe7a-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fe7a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="7fe7a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7fe7a-105">Members</span></span>  
  
|<span data-ttu-id="7fe7a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7fe7a-106">Member</span></span>|<span data-ttu-id="7fe7a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fe7a-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="7fe7a-108">Indica que a variável fornecida é gerada pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="7fe7a-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fe7a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fe7a-109">Requirements</span></span>  
 <span data-ttu-id="7fe7a-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7fe7a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe7a-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="7fe7a-111">See also</span></span>

- [<span data-ttu-id="7fe7a-112">Enumerações de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7fe7a-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
