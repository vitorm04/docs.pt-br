---
title: Enumeração VariableLocationType
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392254efcd099aca60e58b3cc0bc61ca85aa2c66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099944"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="ae031-102">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="ae031-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="ae031-103">Indica o tipo de local nativo de uma variável.</span><span class="sxs-lookup"><span data-stu-id="ae031-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae031-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae031-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="ae031-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ae031-105">Members</span></span>  
  
|<span data-ttu-id="ae031-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ae031-106">Member</span></span>|<span data-ttu-id="ae031-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae031-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="ae031-108">A variável está em um registro.</span><span class="sxs-lookup"><span data-stu-id="ae031-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="ae031-109">A variável está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="ae031-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="ae031-110">A variável não é armazenada em um registro ou um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="ae031-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae031-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae031-111">Remarks</span></span>  
 <span data-ttu-id="ae031-112">Um membro do `VariableLocationType` enumeração é retornada pelo [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ae031-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae031-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae031-113">Requirements</span></span>  
 <span data-ttu-id="ae031-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae031-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae031-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae031-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae031-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae031-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ae031-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ae031-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae031-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae031-118">See also</span></span>

- [<span data-ttu-id="ae031-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="ae031-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
