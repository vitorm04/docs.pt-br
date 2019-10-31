---
title: Enumeração CorDebugGCType
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: b954aa0e4db10fd4b3bde951c7f27d18b8634f5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132191"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="6ee6d-102">Enumeração CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="6ee6d-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="6ee6d-103">Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="6ee6d-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ee6d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ee6d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ee6d-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="6ee6d-106">Membros</span><span class="sxs-lookup"><span data-stu-id="6ee6d-106">Members</span></span>  
  
|<span data-ttu-id="6ee6d-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="6ee6d-107">Member name</span></span>|<span data-ttu-id="6ee6d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ee6d-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="6ee6d-109">O coletor de lixo está em execução em uma estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6ee6d-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="6ee6d-110">O coletor de lixo está em execução em um servidor.</span><span class="sxs-lookup"><span data-stu-id="6ee6d-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ee6d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ee6d-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ee6d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ee6d-112">Requirements</span></span>  
 <span data-ttu-id="6ee6d-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ee6d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ee6d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ee6d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ee6d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ee6d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ee6d-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ee6d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee6d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ee6d-117">See also</span></span>

- [<span data-ttu-id="6ee6d-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6ee6d-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
