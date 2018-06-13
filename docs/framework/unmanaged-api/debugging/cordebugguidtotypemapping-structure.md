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
ms.openlocfilehash: c803a805da605bd52fd50eb1e292c0e277143d7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405253"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="2794a-102">Estrutura CorDebugGuidToTypeMapping</span><span class="sxs-lookup"><span data-stu-id="2794a-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="2794a-103">Mapeia um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID correspondente ao objeto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="2794a-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2794a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2794a-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="2794a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2794a-105">Members</span></span>  
  
|<span data-ttu-id="2794a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2794a-106">Member</span></span>|<span data-ttu-id="2794a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2794a-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="2794a-108">O GUID do cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo.</span><span class="sxs-lookup"><span data-stu-id="2794a-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="2794a-109">Um ponteiro para um objeto de ICorDebugType que fornece informações sobre o tipo de cache.</span><span class="sxs-lookup"><span data-stu-id="2794a-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2794a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2794a-110">Requirements</span></span>  
 <span data-ttu-id="2794a-111">**Plataformas:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2794a-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="2794a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2794a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2794a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2794a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2794a-114">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2794a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2794a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2794a-115">See Also</span></span>  
 [<span data-ttu-id="2794a-116">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="2794a-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="2794a-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="2794a-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
