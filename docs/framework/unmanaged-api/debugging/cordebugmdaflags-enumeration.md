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
ms.openlocfilehash: 34a66a8afa118ecaaaeea0b7b78daaadf1da7509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778268"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="a9953-102">Enumeração CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="a9953-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="a9953-103">Especifica o status do thread no qual o assistente de depuração gerenciada (MDA) é disparado.</span><span class="sxs-lookup"><span data-stu-id="a9953-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9953-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9953-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a9953-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a9953-105">Members</span></span>  
  
|<span data-ttu-id="a9953-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a9953-106">Member</span></span>|<span data-ttu-id="a9953-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9953-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="a9953-108">O thread no qual o MDA foi acionado foi adiado desde que o MDA foi acionado.</span><span class="sxs-lookup"><span data-stu-id="a9953-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9953-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9953-109">Remarks</span></span>  
 <span data-ttu-id="a9953-110">Quando a pilha de chamadas não descreve mais onde o MDA foi gerado originalmente, o thread é considerado como tendo sido *adiado*.</span><span class="sxs-lookup"><span data-stu-id="a9953-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="a9953-111">Essa é uma circunstância incomum apresentada pela execução do thread de uma operação inválida na saída.</span><span class="sxs-lookup"><span data-stu-id="a9953-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9953-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a9953-112">Requirements</span></span>  
 <span data-ttu-id="a9953-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9953-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9953-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9953-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9953-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9953-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9953-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9953-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9953-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="a9953-117">See also</span></span>

- [<span data-ttu-id="a9953-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a9953-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
