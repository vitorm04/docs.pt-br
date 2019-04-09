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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127147"
---
# <a name="userthread-structure"></a><span data-ttu-id="956fd-102">Estrutura USER_THREAD</span><span class="sxs-lookup"><span data-stu-id="956fd-102">USER_THREAD Structure</span></span>
<span data-ttu-id="956fd-103">Fornece informações para um depurador sobre um segmento.</span><span class="sxs-lookup"><span data-stu-id="956fd-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="956fd-104">Para obter mais informações, consulte o [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="956fd-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="956fd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="956fd-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="956fd-106">Membros</span><span class="sxs-lookup"><span data-stu-id="956fd-106">Members</span></span>  
  
|<span data-ttu-id="956fd-107">Membro</span><span class="sxs-lookup"><span data-stu-id="956fd-107">Member</span></span>|<span data-ttu-id="956fd-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="956fd-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="956fd-109">Endereço do buffer de thread.</span><span class="sxs-lookup"><span data-stu-id="956fd-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="956fd-110">Tamanho do buffer de thread, em bytes.</span><span class="sxs-lookup"><span data-stu-id="956fd-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="956fd-111">ID do thread.</span><span class="sxs-lookup"><span data-stu-id="956fd-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="956fd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="956fd-112">Requirements</span></span>  
 <span data-ttu-id="956fd-113">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="956fd-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="956fd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="956fd-114">See also</span></span>

- [<span data-ttu-id="956fd-115">Método SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="956fd-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="956fd-116">Estruturas de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="956fd-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
