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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0191f1fa17d436944fcb590d88dd4004adfa1aba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744294"
---
# <a name="userthread-structure"></a><span data-ttu-id="86503-102">Estrutura USER_THREAD</span><span class="sxs-lookup"><span data-stu-id="86503-102">USER_THREAD Structure</span></span>
<span data-ttu-id="86503-103">Fornece informações para um depurador sobre um segmento.</span><span class="sxs-lookup"><span data-stu-id="86503-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="86503-104">Para obter mais informações, consulte o [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="86503-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86503-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86503-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="86503-106">Membros</span><span class="sxs-lookup"><span data-stu-id="86503-106">Members</span></span>  
  
|<span data-ttu-id="86503-107">Membro</span><span class="sxs-lookup"><span data-stu-id="86503-107">Member</span></span>|<span data-ttu-id="86503-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="86503-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="86503-109">Endereço do buffer de thread.</span><span class="sxs-lookup"><span data-stu-id="86503-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="86503-110">Tamanho do buffer de thread, em bytes.</span><span class="sxs-lookup"><span data-stu-id="86503-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="86503-111">ID do thread.</span><span class="sxs-lookup"><span data-stu-id="86503-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86503-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86503-112">Requirements</span></span>  
 <span data-ttu-id="86503-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="86503-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86503-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86503-114">See also</span></span>

- [<span data-ttu-id="86503-115">Método SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="86503-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="86503-116">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="86503-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
