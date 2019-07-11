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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f101fe2a84a26efb23f57bac3aaf4f0e64a4d36c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740035"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="aca80-102">Enumeração CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="aca80-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="aca80-103">Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="aca80-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aca80-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aca80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aca80-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="aca80-106">Membros</span><span class="sxs-lookup"><span data-stu-id="aca80-106">Members</span></span>  
  
|<span data-ttu-id="aca80-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="aca80-107">Member name</span></span>|<span data-ttu-id="aca80-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="aca80-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="aca80-109">O coletor de lixo está em execução em uma estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="aca80-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="aca80-110">O coletor de lixo está em execução em um servidor.</span><span class="sxs-lookup"><span data-stu-id="aca80-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aca80-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="aca80-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca80-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aca80-112">Requirements</span></span>  
 <span data-ttu-id="aca80-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca80-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca80-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aca80-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aca80-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aca80-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aca80-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca80-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca80-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aca80-117">See also</span></span>

- [<span data-ttu-id="aca80-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="aca80-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
