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
ms.openlocfilehash: 1cc7a299e6be328095c0368acf0a4b767fb74d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="c0acf-102">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="c0acf-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="c0acf-103">Indica o tipo de local nativo de uma variável.</span><span class="sxs-lookup"><span data-stu-id="c0acf-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0acf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0acf-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="c0acf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c0acf-105">Members</span></span>  
  
|<span data-ttu-id="c0acf-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c0acf-106">Member</span></span>|<span data-ttu-id="c0acf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0acf-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="c0acf-108">A variável está em um registro.</span><span class="sxs-lookup"><span data-stu-id="c0acf-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="c0acf-109">A variável está em um local relativo ao registro de memória.</span><span class="sxs-lookup"><span data-stu-id="c0acf-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="c0acf-110">A variável não é armazenada em um registro ou um local de memória relativa de registro.</span><span class="sxs-lookup"><span data-stu-id="c0acf-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0acf-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0acf-111">Remarks</span></span>  
 <span data-ttu-id="c0acf-112">Um membro do `VariableLocationType` retornada pela enumeração o [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c0acf-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0acf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0acf-113">Requirements</span></span>  
 <span data-ttu-id="c0acf-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0acf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0acf-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0acf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0acf-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0acf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0acf-117">**Versões do .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0acf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0acf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0acf-118">See Also</span></span>  
 [<span data-ttu-id="c0acf-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="c0acf-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
