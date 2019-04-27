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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7b9b25673685dde8b75702c80f525515917ae1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915246"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="83ecf-102">Enumeração CorDebugExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="83ecf-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="83ecf-103">Fornece informações adicionais sobre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="83ecf-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ecf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83ecf-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="83ecf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="83ecf-105">Members</span></span>  
  
|<span data-ttu-id="83ecf-106">Membro</span><span class="sxs-lookup"><span data-stu-id="83ecf-106">Member</span></span>|<span data-ttu-id="83ecf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="83ecf-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="83ecf-108">Não há exceção.</span><span class="sxs-lookup"><span data-stu-id="83ecf-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="83ecf-109">A exceção é interceptável.</span><span class="sxs-lookup"><span data-stu-id="83ecf-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="83ecf-110">O momento da exceção pode ainda não ser um que o depurador consiga interceptar.</span><span class="sxs-lookup"><span data-stu-id="83ecf-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="83ecf-111">Por exemplo, se não houver código gerenciado abaixo do retorno de chamada atual ou o evento de exceção resultou de um anexo JIT (Just-In-Time), a exceção não poderá ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="83ecf-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83ecf-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="83ecf-112">Remarks</span></span>  
 <span data-ttu-id="83ecf-113">Novos valores podem ser adicionados a essa enumeração em versões posteriores, assim, você deve preparar um código que use `CorDebugExceptionFlags` para valores imprevistos.</span><span class="sxs-lookup"><span data-stu-id="83ecf-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83ecf-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83ecf-114">Requirements</span></span>  
 <span data-ttu-id="83ecf-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83ecf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83ecf-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83ecf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83ecf-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83ecf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83ecf-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83ecf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ecf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83ecf-119">See also</span></span>

- [<span data-ttu-id="83ecf-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="83ecf-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
