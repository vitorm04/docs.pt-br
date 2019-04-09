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
ms.openlocfilehash: 9dc7093edaf12e801a1e1adc52b0be823ff92b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079910"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="bf708-102">Estrutura CorDebugGuidToTypeMapping</span><span class="sxs-lookup"><span data-stu-id="bf708-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="bf708-103">Mapeia um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID para seu objeto correspondente do ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="bf708-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf708-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf708-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="bf708-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bf708-105">Members</span></span>  
  
|<span data-ttu-id="bf708-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bf708-106">Member</span></span>|<span data-ttu-id="bf708-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf708-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="bf708-108">O GUID do cache no [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo.</span><span class="sxs-lookup"><span data-stu-id="bf708-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="bf708-109">Um ponteiro para um objeto ICorDebugType que fornece informações sobre o tipo de cache.</span><span class="sxs-lookup"><span data-stu-id="bf708-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf708-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf708-110">Requirements</span></span>  
 <span data-ttu-id="bf708-111">**Plataformas:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf708-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="bf708-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf708-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf708-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf708-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bf708-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bf708-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf708-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf708-115">See also</span></span>

- [<span data-ttu-id="bf708-116">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="bf708-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="bf708-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="bf708-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
