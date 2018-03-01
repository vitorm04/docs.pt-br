---
title: "Enumeração CorDebugGCType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2045c2edd129c2e4154d24b43d96f6ea8ad64cab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="a803c-102">Enumeração CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="a803c-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="a803c-103">Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="a803c-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a803c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a803c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a803c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a803c-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="a803c-106">Membros</span><span class="sxs-lookup"><span data-stu-id="a803c-106">Members</span></span>  
  
|<span data-ttu-id="a803c-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="a803c-107">Member name</span></span>|<span data-ttu-id="a803c-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a803c-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="a803c-109">O coletor de lixo é executado em uma estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a803c-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="a803c-110">O coletor de lixo está em execução em um servidor.</span><span class="sxs-lookup"><span data-stu-id="a803c-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a803c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a803c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a803c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a803c-112">Requirements</span></span>  
 <span data-ttu-id="a803c-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a803c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a803c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a803c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a803c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a803c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a803c-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a803c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a803c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a803c-117">See Also</span></span>  
 [<span data-ttu-id="a803c-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a803c-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
