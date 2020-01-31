---
title: Enumeração CorDebugJITCompilerFlags
ms.date: 03/30/2017
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
ms.openlocfilehash: 65d7e830b82cc1780826517fe8cff1da0a7d6188
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793902"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="710aa-102">Enumeração CorDebugJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="710aa-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="710aa-103">Contém valores que influenciam o comportamento do compilador just-in-time (JIT) gerenciado.</span><span class="sxs-lookup"><span data-stu-id="710aa-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="710aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="710aa-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="710aa-105">Membros</span><span class="sxs-lookup"><span data-stu-id="710aa-105">Members</span></span>  
  
|<span data-ttu-id="710aa-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="710aa-106">Member</span></span>|<span data-ttu-id="710aa-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="710aa-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="710aa-108">Especifica que o compilador deve controlar os dados de compilação e permite otimizações.</span><span class="sxs-lookup"><span data-stu-id="710aa-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="710aa-109">Especifica que o compilador deve controlar os dados de compilação, mas desabilita otimizações.</span><span class="sxs-lookup"><span data-stu-id="710aa-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="710aa-110">Especifica que o compilador deve controlar os dados de compilação, desabilitar otimizações e habilitar as tecnologias editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="710aa-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="710aa-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="710aa-111">Requirements</span></span>  
 <span data-ttu-id="710aa-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="710aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="710aa-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="710aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="710aa-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="710aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="710aa-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="710aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="710aa-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="710aa-116">See also</span></span>

- [<span data-ttu-id="710aa-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="710aa-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
