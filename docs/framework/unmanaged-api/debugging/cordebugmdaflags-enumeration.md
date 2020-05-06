---
title: Enumeração CorDebugMDAFlags
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: e024500ea66dcb42e712e07e976a709401160a27
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795762"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="98087-102">Enumeração CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="98087-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="98087-103">Especifica o status do thread no qual o assistente de depuração gerenciada (MDA) é disparado.</span><span class="sxs-lookup"><span data-stu-id="98087-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98087-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98087-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="98087-105">Membros</span><span class="sxs-lookup"><span data-stu-id="98087-105">Members</span></span>  
  
|<span data-ttu-id="98087-106">Membro</span><span class="sxs-lookup"><span data-stu-id="98087-106">Member</span></span>|<span data-ttu-id="98087-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="98087-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="98087-108">O thread no qual o MDA foi acionado foi adiado desde que o MDA foi acionado.</span><span class="sxs-lookup"><span data-stu-id="98087-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98087-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="98087-109">Remarks</span></span>  
 <span data-ttu-id="98087-110">Quando a pilha de chamadas não descreve mais onde o MDA foi gerado originalmente, o thread é considerado como tendo sido *adiado*.</span><span class="sxs-lookup"><span data-stu-id="98087-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="98087-111">Essa é uma circunstância incomum apresentada pela execução do thread de uma operação inválida na saída.</span><span class="sxs-lookup"><span data-stu-id="98087-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98087-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98087-112">Requirements</span></span>  
 <span data-ttu-id="98087-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98087-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98087-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98087-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98087-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98087-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98087-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98087-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98087-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98087-117">See also</span></span>

- [<span data-ttu-id="98087-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="98087-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
