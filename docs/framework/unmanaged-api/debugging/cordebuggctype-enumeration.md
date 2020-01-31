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
ms.openlocfilehash: 6f4c96517375df4cd249b72953bf37812a498c0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789356"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="24613-102">Enumeração CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="24613-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="24613-103">Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="24613-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24613-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24613-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="24613-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24613-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="24613-106">Membros</span><span class="sxs-lookup"><span data-stu-id="24613-106">Members</span></span>  
  
|<span data-ttu-id="24613-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="24613-107">Member name</span></span>|<span data-ttu-id="24613-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="24613-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="24613-109">O coletor de lixo está em execução em uma estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="24613-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="24613-110">O coletor de lixo está em execução em um servidor.</span><span class="sxs-lookup"><span data-stu-id="24613-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24613-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="24613-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24613-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="24613-112">Requirements</span></span>  
 <span data-ttu-id="24613-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24613-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24613-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24613-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24613-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24613-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24613-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24613-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24613-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="24613-117">See also</span></span>

- [<span data-ttu-id="24613-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="24613-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
