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
ms.openlocfilehash: 0c797378f5e13f39c1c786237a3a7b9cf577fccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198849"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="f24f9-102">Enumeração CorSymVarFlag</span><span class="sxs-lookup"><span data-stu-id="f24f9-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="f24f9-103">Indica se uma variável é gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="f24f9-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f24f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f24f9-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="f24f9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f24f9-105">Members</span></span>  
  
|<span data-ttu-id="f24f9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f24f9-106">Member</span></span>|<span data-ttu-id="f24f9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f24f9-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="f24f9-108">Indica que a variável fornecida é gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="f24f9-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f24f9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f24f9-109">Requirements</span></span>  
 <span data-ttu-id="f24f9-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f24f9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24f9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f24f9-111">See also</span></span>

- [<span data-ttu-id="f24f9-112">Enumerações de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="f24f9-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
