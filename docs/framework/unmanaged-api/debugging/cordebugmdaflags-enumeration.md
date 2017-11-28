---
title: "Enumeração CorDebugMDAFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMDAFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMDAFlags
helpviewer_keywords: CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 827825e4012b421caa4e05702a6f1a1b863ac69d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="e589b-102">Enumeração CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="e589b-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="e589b-103">Especifica o status do thread no qual o assistente de depuração gerenciada (MDA) é disparado.</span><span class="sxs-lookup"><span data-stu-id="e589b-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e589b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e589b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e589b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e589b-105">Members</span></span>  
  
|<span data-ttu-id="e589b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e589b-106">Member</span></span>|<span data-ttu-id="e589b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e589b-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="e589b-108">O thread em que o MDA foi acionado passou desde o MDA foi acionado.</span><span class="sxs-lookup"><span data-stu-id="e589b-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e589b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e589b-109">Remarks</span></span>  
 <span data-ttu-id="e589b-110">Quando a pilha de chamadas não descreve onde o MDA foi gerado originalmente, o thread é considerado como tendo *adiadas*.</span><span class="sxs-lookup"><span data-stu-id="e589b-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="e589b-111">Esta é uma circunstância incomum provocada pela execução do thread de uma operação inválida ao sair.</span><span class="sxs-lookup"><span data-stu-id="e589b-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e589b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e589b-112">Requirements</span></span>  
 <span data-ttu-id="e589b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e589b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e589b-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e589b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e589b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e589b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e589b-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e589b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e589b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e589b-117">See Also</span></span>  
 [<span data-ttu-id="e589b-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="e589b-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
