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
ms.openlocfilehash: f8d6b16f3eeb32e41f3568e0b237f18c945a8cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423891"
---
# <a name="callid-structure"></a><span data-ttu-id="e85d4-102">Estrutura CALL_ID</span><span class="sxs-lookup"><span data-stu-id="e85d4-102">CALL_ID Structure</span></span>
<span data-ttu-id="e85d4-103">Fornece informações para um depurador sobre uma função que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="e85d4-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="e85d4-104">Consulte o [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e85d4-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85d4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e85d4-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e85d4-106">Membros</span><span class="sxs-lookup"><span data-stu-id="e85d4-106">Members</span></span>  
  
|<span data-ttu-id="e85d4-107">Membro</span><span class="sxs-lookup"><span data-stu-id="e85d4-107">Member</span></span>|<span data-ttu-id="e85d4-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e85d4-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="e85d4-109">Identifica o computador que está fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="e85d4-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="e85d4-110">Identifica o processador de máquina.</span><span class="sxs-lookup"><span data-stu-id="e85d4-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="e85d4-111">Identifica o thread que está executando a chamada.</span><span class="sxs-lookup"><span data-stu-id="e85d4-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="e85d4-112">Especifica o endereço da pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="e85d4-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="e85d4-113">Especifica o endereço da chamada.</span><span class="sxs-lookup"><span data-stu-id="e85d4-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="e85d4-114">Identifica o computador que executará a chamada.</span><span class="sxs-lookup"><span data-stu-id="e85d4-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e85d4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e85d4-115">Requirements</span></span>  
 <span data-ttu-id="e85d4-116">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e85d4-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85d4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e85d4-117">See Also</span></span>  
 [<span data-ttu-id="e85d4-118">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="e85d4-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="e85d4-119">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="e85d4-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
