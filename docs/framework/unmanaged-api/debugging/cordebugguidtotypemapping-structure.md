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
ms.openlocfilehash: 313f6649448653ad630d616c7dbf739653e352dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132834"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="eadab-102">Estrutura CorDebugGuidToTypeMapping</span><span class="sxs-lookup"><span data-stu-id="eadab-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="eadab-103">Mapeia um GUID de Windows Runtime para seu objeto ICorDebugType correspondente.</span><span class="sxs-lookup"><span data-stu-id="eadab-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eadab-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="eadab-105">Membros</span><span class="sxs-lookup"><span data-stu-id="eadab-105">Members</span></span>  
  
|<span data-ttu-id="eadab-106">Membro</span><span class="sxs-lookup"><span data-stu-id="eadab-106">Member</span></span>|<span data-ttu-id="eadab-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eadab-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="eadab-108">O GUID do tipo de Windows Runtime em cache.</span><span class="sxs-lookup"><span data-stu-id="eadab-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="eadab-109">Um ponteiro para um objeto ICorDebugType que fornece informações sobre o tipo armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="eadab-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eadab-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eadab-110">Requirements</span></span>  
 <span data-ttu-id="eadab-111">**Plataformas:** Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="eadab-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="eadab-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eadab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eadab-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eadab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eadab-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eadab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadab-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eadab-115">See also</span></span>

- [<span data-ttu-id="eadab-116">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="eadab-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="eadab-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="eadab-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
