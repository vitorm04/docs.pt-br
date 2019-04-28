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
ms.openlocfilehash: 11551221732e454e48111d48d60ca9b72f7f9b66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914700"
---
# <a name="userthread-structure"></a><span data-ttu-id="b8498-102">Estrutura USER_THREAD</span><span class="sxs-lookup"><span data-stu-id="b8498-102">USER_THREAD Structure</span></span>
<span data-ttu-id="b8498-103">Fornece informações para um depurador sobre um segmento.</span><span class="sxs-lookup"><span data-stu-id="b8498-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="b8498-104">Para obter mais informações, consulte o [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b8498-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8498-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8498-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="b8498-106">Membros</span><span class="sxs-lookup"><span data-stu-id="b8498-106">Members</span></span>  
  
|<span data-ttu-id="b8498-107">Membro</span><span class="sxs-lookup"><span data-stu-id="b8498-107">Member</span></span>|<span data-ttu-id="b8498-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8498-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="b8498-109">Endereço do buffer de thread.</span><span class="sxs-lookup"><span data-stu-id="b8498-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="b8498-110">Tamanho do buffer de thread, em bytes.</span><span class="sxs-lookup"><span data-stu-id="b8498-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="b8498-111">ID do thread.</span><span class="sxs-lookup"><span data-stu-id="b8498-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8498-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8498-112">Requirements</span></span>  
 <span data-ttu-id="b8498-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b8498-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8498-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8498-114">See also</span></span>

- [<span data-ttu-id="b8498-115">Método SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="b8498-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="b8498-116">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b8498-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
