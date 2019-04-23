---
title: Enumeração COR_PRF_CLAUSE_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 861f4c18f4c5151dc7215d300775928b88f018aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090622"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="e9eab-102">Enumeração COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e9eab-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="e9eab-103">Indica o tipo de cláusula de exceção que o código acabou de inserir ou deixar.</span><span class="sxs-lookup"><span data-stu-id="e9eab-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9eab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9eab-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="e9eab-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e9eab-105">Members</span></span>  
  
|<span data-ttu-id="e9eab-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e9eab-106">Member</span></span>|<span data-ttu-id="e9eab-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9eab-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="e9eab-108">A cláusula de exceção não é válida.</span><span class="sxs-lookup"><span data-stu-id="e9eab-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="e9eab-109">A cláusula de exceção é uma expressão de filtro.</span><span class="sxs-lookup"><span data-stu-id="e9eab-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="e9eab-110">A cláusula de exceção é um `catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="e9eab-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="e9eab-111">A cláusula de exceção é um `finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="e9eab-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9eab-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9eab-112">Requirements</span></span>  
 <span data-ttu-id="e9eab-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9eab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9eab-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9eab-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9eab-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9eab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9eab-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9eab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9eab-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9eab-117">See also</span></span>

- [<span data-ttu-id="e9eab-118">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="e9eab-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
