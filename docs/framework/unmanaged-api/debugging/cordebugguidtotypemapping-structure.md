---
title: Estrutura CorDebugGuidToTypeMapping
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e1b19d6340f559e6f8b7e0f7bc042a10df16c3
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025992"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="acde6-102">Estrutura CorDebugGuidToTypeMapping</span><span class="sxs-lookup"><span data-stu-id="acde6-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="acde6-103">Mapeia um GUID de tempo de execução do Windows para seu objeto correspondente do ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="acde6-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acde6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acde6-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="acde6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="acde6-105">Members</span></span>  
  
|<span data-ttu-id="acde6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="acde6-106">Member</span></span>|<span data-ttu-id="acde6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="acde6-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="acde6-108">O GUID do tipo de tempo de execução do Windows em cache.</span><span class="sxs-lookup"><span data-stu-id="acde6-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="acde6-109">Um ponteiro para um objeto ICorDebugType que fornece informações sobre o tipo de cache.</span><span class="sxs-lookup"><span data-stu-id="acde6-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acde6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acde6-110">Requirements</span></span>  
 <span data-ttu-id="acde6-111">**Plataformas:** Tempo de execução do Windows.</span><span class="sxs-lookup"><span data-stu-id="acde6-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="acde6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acde6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acde6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acde6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acde6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acde6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acde6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acde6-115">See also</span></span>

- [<span data-ttu-id="acde6-116">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="acde6-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="acde6-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="acde6-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
