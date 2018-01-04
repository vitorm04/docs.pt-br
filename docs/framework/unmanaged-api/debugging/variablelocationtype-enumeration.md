---
title: "Enumeração VariableLocationType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: VariableLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: VariableLocationType
helpviewer_keywords: VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ea476ef32b807823108aa2836778da576618214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="bdfb7-102">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="bdfb7-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="bdfb7-103">Indica o tipo de local nativo de uma variável.</span><span class="sxs-lookup"><span data-stu-id="bdfb7-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdfb7-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="bdfb7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bdfb7-105">Members</span></span>  
  
|<span data-ttu-id="bdfb7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bdfb7-106">Member</span></span>|<span data-ttu-id="bdfb7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdfb7-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="bdfb7-108">A variável está em um registro.</span><span class="sxs-lookup"><span data-stu-id="bdfb7-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="bdfb7-109">A variável está em um local relativo ao registro de memória.</span><span class="sxs-lookup"><span data-stu-id="bdfb7-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="bdfb7-110">A variável não é armazenada em um registro ou um local de memória relativa de registro.</span><span class="sxs-lookup"><span data-stu-id="bdfb7-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdfb7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdfb7-111">Remarks</span></span>  
 <span data-ttu-id="bdfb7-112">Um membro do `VariableLocationType` retornada pela enumeração o [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bdfb7-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdfb7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdfb7-113">Requirements</span></span>  
 <span data-ttu-id="bdfb7-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdfb7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfb7-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdfb7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdfb7-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdfb7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdfb7-117">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfb7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfb7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdfb7-118">See Also</span></span>  
 [<span data-ttu-id="bdfb7-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="bdfb7-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
