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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac4a8a0c13ba6aa0d5c65ec7fa1aa3b771c964eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="b9778-102">Enumeração CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="b9778-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="b9778-103">Especifica o status do thread no qual o assistente de depuração gerenciada (MDA) é disparado.</span><span class="sxs-lookup"><span data-stu-id="b9778-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9778-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9778-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b9778-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b9778-105">Members</span></span>  
  
|<span data-ttu-id="b9778-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b9778-106">Member</span></span>|<span data-ttu-id="b9778-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9778-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="b9778-108">O thread em que o MDA foi acionado passou desde o MDA foi acionado.</span><span class="sxs-lookup"><span data-stu-id="b9778-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9778-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9778-109">Remarks</span></span>  
 <span data-ttu-id="b9778-110">Quando a pilha de chamadas não descreve onde o MDA foi gerado originalmente, o thread é considerado como tendo *adiadas*.</span><span class="sxs-lookup"><span data-stu-id="b9778-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="b9778-111">Esta é uma circunstância incomum provocada pela execução do thread de uma operação inválida ao sair.</span><span class="sxs-lookup"><span data-stu-id="b9778-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9778-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9778-112">Requirements</span></span>  
 <span data-ttu-id="b9778-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9778-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9778-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9778-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9778-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9778-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9778-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9778-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9778-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9778-117">See Also</span></span>  
 [<span data-ttu-id="b9778-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b9778-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
