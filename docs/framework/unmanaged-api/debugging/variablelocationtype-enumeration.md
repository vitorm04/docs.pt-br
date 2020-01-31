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
ms.openlocfilehash: 1aa59ee559abff8006f0ac63a812e4315aa48154
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790306"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="b7bf8-102">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="b7bf8-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="b7bf8-103">Indica o tipo de local nativo de uma variável.</span><span class="sxs-lookup"><span data-stu-id="b7bf8-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bf8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7bf8-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="b7bf8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b7bf8-105">Members</span></span>  
  
|<span data-ttu-id="b7bf8-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b7bf8-106">Member</span></span>|<span data-ttu-id="b7bf8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7bf8-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="b7bf8-108">A variável está em um registro.</span><span class="sxs-lookup"><span data-stu-id="b7bf8-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="b7bf8-109">A variável está em um local de memória relativa ao registro.</span><span class="sxs-lookup"><span data-stu-id="b7bf8-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="b7bf8-110">A variável não é armazenada em um local de memória de registro ou de registro relativo.</span><span class="sxs-lookup"><span data-stu-id="b7bf8-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7bf8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7bf8-111">Remarks</span></span>  
 <span data-ttu-id="b7bf8-112">Um membro da enumeração `VariableLocationType` é retornado pelo método [ICorDebugVariableHome:: Getlocationtype](icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b7bf8-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7bf8-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b7bf8-113">Requirements</span></span>  
 <span data-ttu-id="b7bf8-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7bf8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7bf8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7bf8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7bf8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7bf8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7bf8-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7bf8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bf8-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="b7bf8-118">See also</span></span>

- [<span data-ttu-id="b7bf8-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b7bf8-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
