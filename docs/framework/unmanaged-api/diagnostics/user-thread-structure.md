---
title: Estrutura USER_THREAD
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609437"
---
# <a name="user_thread-structure"></a><span data-ttu-id="457f5-102">Estrutura USER_THREAD</span><span class="sxs-lookup"><span data-stu-id="457f5-102">USER_THREAD Structure</span></span>
<span data-ttu-id="457f5-103">Fornece informações para um depurador sobre um thread.</span><span class="sxs-lookup"><span data-stu-id="457f5-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="457f5-104">Para obter mais informações, consulte o método [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="457f5-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457f5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="457f5-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="457f5-106">Membros</span><span class="sxs-lookup"><span data-stu-id="457f5-106">Members</span></span>  
  
|<span data-ttu-id="457f5-107">Membro</span><span class="sxs-lookup"><span data-stu-id="457f5-107">Member</span></span>|<span data-ttu-id="457f5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="457f5-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="457f5-109">Endereço do buffer de thread.</span><span class="sxs-lookup"><span data-stu-id="457f5-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="457f5-110">Comprimento do buffer de thread, em bytes.</span><span class="sxs-lookup"><span data-stu-id="457f5-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="457f5-111">ID do thread.</span><span class="sxs-lookup"><span data-stu-id="457f5-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="457f5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="457f5-112">Requirements</span></span>  
 <span data-ttu-id="457f5-113">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="457f5-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457f5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="457f5-114">See also</span></span>

- [<span data-ttu-id="457f5-115">Método SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="457f5-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="457f5-116">Estruturas de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="457f5-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
