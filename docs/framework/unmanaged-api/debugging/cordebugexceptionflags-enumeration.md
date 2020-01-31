---
title: Enumeração CorDebugExceptionFlags
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: 6ef81e224f3573021ee96ac313ec4923928dedad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789395"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="6328e-102">Enumeração CorDebugExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="6328e-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="6328e-103">Fornece informações adicionais sobre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6328e-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6328e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6328e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6328e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6328e-105">Members</span></span>  
  
|<span data-ttu-id="6328e-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6328e-106">Member</span></span>|<span data-ttu-id="6328e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6328e-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="6328e-108">Não há exceção.</span><span class="sxs-lookup"><span data-stu-id="6328e-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="6328e-109">A exceção é interceptável.</span><span class="sxs-lookup"><span data-stu-id="6328e-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="6328e-110">O momento da exceção pode ainda não ser um que o depurador consiga interceptar.</span><span class="sxs-lookup"><span data-stu-id="6328e-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="6328e-111">Por exemplo, se não houver código gerenciado abaixo do retorno de chamada atual ou o evento de exceção resultou de um anexo JIT (Just-In-Time), a exceção não poderá ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="6328e-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6328e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="6328e-112">Remarks</span></span>  
 <span data-ttu-id="6328e-113">Novos valores podem ser adicionados a essa enumeração em versões posteriores, assim, você deve preparar um código que use `CorDebugExceptionFlags` para valores imprevistos.</span><span class="sxs-lookup"><span data-stu-id="6328e-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6328e-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="6328e-114">Requirements</span></span>  
 <span data-ttu-id="6328e-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6328e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6328e-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6328e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6328e-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6328e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6328e-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6328e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6328e-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="6328e-119">See also</span></span>

- [<span data-ttu-id="6328e-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6328e-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
