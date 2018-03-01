---
title: "Enumeração CorDebugJITCompilerFlags"
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
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dfb78a160a7a6b9f50174fc8bb177cfd8d3f9383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="618a1-102">Enumeração CorDebugJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="618a1-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="618a1-103">Contém valores que influenciam o comportamento do compilador just-in-time (JIT) gerenciado.</span><span class="sxs-lookup"><span data-stu-id="618a1-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="618a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="618a1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="618a1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="618a1-105">Members</span></span>  
  
|<span data-ttu-id="618a1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="618a1-106">Member</span></span>|<span data-ttu-id="618a1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="618a1-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="618a1-108">Especifica que o compilador deve controlar dados de compilação e permite otimizações.</span><span class="sxs-lookup"><span data-stu-id="618a1-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="618a1-109">Especifica que o compilador deve controlar dados de compilação, mas desabilita otimizações.</span><span class="sxs-lookup"><span data-stu-id="618a1-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="618a1-110">Especifica que o compilador deve controlar dados de compilação, desabilita otimizações, e permite editar e continuar tecnologias.</span><span class="sxs-lookup"><span data-stu-id="618a1-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="618a1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="618a1-111">Requirements</span></span>  
 <span data-ttu-id="618a1-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="618a1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="618a1-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="618a1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="618a1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="618a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="618a1-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="618a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="618a1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="618a1-116">See Also</span></span>  
 [<span data-ttu-id="618a1-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="618a1-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
