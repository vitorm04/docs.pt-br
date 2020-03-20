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
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178355"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="b7bfd-102">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="b7bfd-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="b7bfd-103">Indica o tipo de localização nativa de uma variável.</span><span class="sxs-lookup"><span data-stu-id="b7bfd-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bfd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7bfd-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="b7bfd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b7bfd-105">Members</span></span>  
  
|<span data-ttu-id="b7bfd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b7bfd-106">Member</span></span>|<span data-ttu-id="b7bfd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7bfd-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="b7bfd-108">A variável está em um registro.</span><span class="sxs-lookup"><span data-stu-id="b7bfd-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="b7bfd-109">A variável está em um registro de registro de memória relativa.</span><span class="sxs-lookup"><span data-stu-id="b7bfd-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="b7bfd-110">A variável não é armazenada em um registro ou em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="b7bfd-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7bfd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7bfd-111">Remarks</span></span>  
 <span data-ttu-id="b7bfd-112">Um membro `VariableLocationType` da enumeração é retornado pelo método [ICorDebugVariableHome::GetLocationType.](icordebugvariablehome-getlocationtype-method.md)</span><span class="sxs-lookup"><span data-stu-id="b7bfd-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7bfd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7bfd-113">Requirements</span></span>  
 <span data-ttu-id="b7bfd-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7bfd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7bfd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7bfd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7bfd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7bfd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7bfd-117">**.NET Framework Versions:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7bfd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bfd-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7bfd-118">See also</span></span>

- [<span data-ttu-id="b7bfd-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b7bfd-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
