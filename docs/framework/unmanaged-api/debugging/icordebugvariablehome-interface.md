---
title: Interface ICorDebugVariableHome
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: 306a07450b8ae6d29875ca0cc4679390472e4d1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121035"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="6cf56-102">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="6cf56-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="6cf56-103">Representa uma variável local ou um argumento de uma função.</span><span class="sxs-lookup"><span data-stu-id="6cf56-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cf56-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6cf56-104">Methods</span></span>  
  
|<span data-ttu-id="6cf56-105">Método</span><span class="sxs-lookup"><span data-stu-id="6cf56-105">Method</span></span>|<span data-ttu-id="6cf56-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cf56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cf56-107">Método GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="6cf56-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="6cf56-108">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="6cf56-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="6cf56-109">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="6cf56-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="6cf56-110">Obtém a instância "ICorDebugCode" que contém este objeto de `ICorDebugVariableHome`.</span><span class="sxs-lookup"><span data-stu-id="6cf56-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="6cf56-111">Método GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="6cf56-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="6cf56-112">Obtém o intervalo nativo no qual essa variável está ativa.</span><span class="sxs-lookup"><span data-stu-id="6cf56-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="6cf56-113">Método GetLocationType</span><span class="sxs-lookup"><span data-stu-id="6cf56-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="6cf56-114">Obtém o tipo do local nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="6cf56-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="6cf56-115">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="6cf56-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="6cf56-116">Obtém o deslocamento do registro base de uma variável.</span><span class="sxs-lookup"><span data-stu-id="6cf56-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="6cf56-117">Método GetRegister</span><span class="sxs-lookup"><span data-stu-id="6cf56-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="6cf56-118">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="6cf56-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="6cf56-119">Método GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="6cf56-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="6cf56-120">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="6cf56-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6cf56-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cf56-121">Example</span></span>  
 <span data-ttu-id="6cf56-122">O fragmento de código a seguir usa o objeto [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) chamado `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="6cf56-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="6cf56-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cf56-123">Requirements</span></span>  
 <span data-ttu-id="6cf56-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf56-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf56-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cf56-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cf56-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cf56-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cf56-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf56-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf56-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cf56-128">See also</span></span>

- [<span data-ttu-id="6cf56-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6cf56-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6cf56-130">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="6cf56-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
