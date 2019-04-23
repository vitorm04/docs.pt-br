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
ms.openlocfilehash: 315d6dd522f3c6be2d36b1eb411d9f471350df60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182917"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="f60d8-102">Enumeração CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="f60d8-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="f60d8-103">Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="f60d8-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f60d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f60d8-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f60d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f60d8-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="f60d8-106">Membros</span><span class="sxs-lookup"><span data-stu-id="f60d8-106">Members</span></span>  
  
|<span data-ttu-id="f60d8-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="f60d8-107">Member name</span></span>|<span data-ttu-id="f60d8-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f60d8-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="f60d8-109">O coletor de lixo está em execução em uma estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f60d8-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="f60d8-110">O coletor de lixo está em execução em um servidor.</span><span class="sxs-lookup"><span data-stu-id="f60d8-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f60d8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f60d8-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f60d8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f60d8-112">Requirements</span></span>  
 <span data-ttu-id="f60d8-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f60d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f60d8-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f60d8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f60d8-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f60d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f60d8-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f60d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60d8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f60d8-117">See also</span></span>

- [<span data-ttu-id="f60d8-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="f60d8-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
