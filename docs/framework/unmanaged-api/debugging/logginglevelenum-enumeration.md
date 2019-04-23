---
title: Enumeração LoggingLevelEnum
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086501"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="fbdd8-102">Enumeração LoggingLevelEnum</span><span class="sxs-lookup"><span data-stu-id="fbdd8-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="fbdd8-103">Indica o nível de severidade de uma mensagem descritiva que é escrita no log de eventos quando um thread gerenciado registrar um evento.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbdd8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbdd8-104">Syntax</span></span>  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="fbdd8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fbdd8-105">Members</span></span>  
  
|<span data-ttu-id="fbdd8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fbdd8-106">Member</span></span>|<span data-ttu-id="fbdd8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbdd8-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="fbdd8-108">A mensagem é um nível de rastreamento, 0.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="fbdd8-109">A mensagem é um nível de rastreamento 1.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="fbdd8-110">A mensagem é um nível de rastreamento 2.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="fbdd8-111">A mensagem é um nível de rastreamento 3.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="fbdd8-112">A mensagem é um nível de rastreamento 4.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="fbdd8-113">A mensagem é um nível de status 0.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="fbdd8-114">A mensagem é um nível de status 1.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="fbdd8-115">A mensagem é um nível de status 2.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="fbdd8-116">A mensagem é um nível de status 3.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="fbdd8-117">A mensagem é um nível de status 4.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="fbdd8-118">A mensagem é um nível de aviso.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="fbdd8-119">A mensagem é um nível de erro.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="fbdd8-120">A mensagem é um nível de pânico.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbdd8-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbdd8-121">Remarks</span></span>  
 <span data-ttu-id="fbdd8-122">O common language runtime (CLR) chama o [icordebugmanagedcallback:: Logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) método para notificar o depurador que um thread gerenciado fez um evento.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="fbdd8-123">O CLR passa o valor de `LoggingLevelEnum` enumeração para indicar o nível de severidade da mensagem que o thread gerenciado gravou o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="fbdd8-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbdd8-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbdd8-124">Requirements</span></span>  
 <span data-ttu-id="fbdd8-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbdd8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbdd8-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbdd8-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbdd8-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbdd8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbdd8-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbdd8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbdd8-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbdd8-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="fbdd8-130">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="fbdd8-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
