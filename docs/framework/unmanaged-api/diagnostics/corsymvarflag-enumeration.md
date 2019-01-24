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
ms.openlocfilehash: 50367358ba5bcf335f8cc2ca3222f6cf7ea2ff70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670128"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="a32c2-102">Enumeração CorSymVarFlag</span><span class="sxs-lookup"><span data-stu-id="a32c2-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="a32c2-103">Indica se uma variável é gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="a32c2-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a32c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a32c2-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="a32c2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a32c2-105">Members</span></span>  
  
|<span data-ttu-id="a32c2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a32c2-106">Member</span></span>|<span data-ttu-id="a32c2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a32c2-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="a32c2-108">Indica que a variável fornecida é gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="a32c2-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a32c2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a32c2-109">Requirements</span></span>  
 <span data-ttu-id="a32c2-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a32c2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a32c2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a32c2-111">See also</span></span>
- [<span data-ttu-id="a32c2-112">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="a32c2-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
