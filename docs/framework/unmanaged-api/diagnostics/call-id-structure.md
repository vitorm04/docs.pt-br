---
title: Estrutura CALL_ID
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
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71fd69cbcced1440839b9eedf8fbe3d8f5b90646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="callid-structure"></a><span data-ttu-id="2e089-102">Estrutura CALL_ID</span><span class="sxs-lookup"><span data-stu-id="2e089-102">CALL_ID Structure</span></span>
<span data-ttu-id="2e089-103">Fornece informações para um depurador sobre uma função que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="2e089-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="2e089-104">Consulte o [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2e089-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e089-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e089-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="2e089-106">Membros</span><span class="sxs-lookup"><span data-stu-id="2e089-106">Members</span></span>  
  
|<span data-ttu-id="2e089-107">Membro</span><span class="sxs-lookup"><span data-stu-id="2e089-107">Member</span></span>|<span data-ttu-id="2e089-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e089-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="2e089-109">Identifica o computador que está fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="2e089-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="2e089-110">Identifica o processador de máquina.</span><span class="sxs-lookup"><span data-stu-id="2e089-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="2e089-111">Identifica o thread que está executando a chamada.</span><span class="sxs-lookup"><span data-stu-id="2e089-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="2e089-112">Especifica o endereço da pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="2e089-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="2e089-113">Especifica o endereço da chamada.</span><span class="sxs-lookup"><span data-stu-id="2e089-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="2e089-114">Identifica o computador que executará a chamada.</span><span class="sxs-lookup"><span data-stu-id="2e089-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e089-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e089-115">Requirements</span></span>  
 <span data-ttu-id="2e089-116">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="2e089-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e089-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e089-117">See Also</span></span>  
 [<span data-ttu-id="2e089-118">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="2e089-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="2e089-119">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="2e089-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
