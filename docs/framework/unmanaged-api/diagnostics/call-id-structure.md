---
title: Estrutura CALL_ID
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6fa729b131d12b2825a2def700fd918ce8acc40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986473"
---
# <a name="callid-structure"></a><span data-ttu-id="41d5d-102">Estrutura CALL_ID</span><span class="sxs-lookup"><span data-stu-id="41d5d-102">CALL_ID Structure</span></span>
<span data-ttu-id="41d5d-103">Fornece informações para um depurador sobre uma função que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="41d5d-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="41d5d-104">Consulte a [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="41d5d-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d5d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41d5d-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="41d5d-106">Membros</span><span class="sxs-lookup"><span data-stu-id="41d5d-106">Members</span></span>  
  
|<span data-ttu-id="41d5d-107">Membro</span><span class="sxs-lookup"><span data-stu-id="41d5d-107">Member</span></span>|<span data-ttu-id="41d5d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="41d5d-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="41d5d-109">Identifica o computador que está fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="41d5d-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="41d5d-110">Identifica o processador de máquina.</span><span class="sxs-lookup"><span data-stu-id="41d5d-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="41d5d-111">Identifica o thread que está executando a chamada.</span><span class="sxs-lookup"><span data-stu-id="41d5d-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="41d5d-112">Especifica o endereço da pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="41d5d-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="41d5d-113">Especifica o endereço da chamada.</span><span class="sxs-lookup"><span data-stu-id="41d5d-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="41d5d-114">Identifica o computador que executará a chamada.</span><span class="sxs-lookup"><span data-stu-id="41d5d-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41d5d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41d5d-115">Requirements</span></span>  
 <span data-ttu-id="41d5d-116">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="41d5d-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d5d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41d5d-117">See also</span></span>

- [<span data-ttu-id="41d5d-118">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="41d5d-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="41d5d-119">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="41d5d-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
