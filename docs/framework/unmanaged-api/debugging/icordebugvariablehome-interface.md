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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae11cdbbdb0fa63d1b903d18aff133344fd17f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422527"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="a8c36-102">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="a8c36-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="a8c36-103">Representa um argumento de uma função ou variável local.</span><span class="sxs-lookup"><span data-stu-id="a8c36-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8c36-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a8c36-104">Methods</span></span>  
  
|<span data-ttu-id="a8c36-105">Método</span><span class="sxs-lookup"><span data-stu-id="a8c36-105">Method</span></span>|<span data-ttu-id="a8c36-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8c36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8c36-107">Método GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="a8c36-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="a8c36-108">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="a8c36-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="a8c36-109">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="a8c36-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="a8c36-110">Obtém a instância de "ICorDebugCode" que contém essa `ICorDebugVariableHome` objeto.</span><span class="sxs-lookup"><span data-stu-id="a8c36-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="a8c36-111">Método GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="a8c36-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="a8c36-112">Obtém o intervalo nativo através da qual esta variável está ativo.</span><span class="sxs-lookup"><span data-stu-id="a8c36-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="a8c36-113">Método GetLocationType</span><span class="sxs-lookup"><span data-stu-id="a8c36-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="a8c36-114">Obtém o tipo de local nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="a8c36-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="a8c36-115">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="a8c36-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="a8c36-116">Obtém o deslocamento do registro base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="a8c36-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="a8c36-117">Método GetRegister</span><span class="sxs-lookup"><span data-stu-id="a8c36-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="a8c36-118">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="a8c36-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="a8c36-119">Método GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="a8c36-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="a8c36-120">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="a8c36-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a8c36-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8c36-121">Example</span></span>  
 <span data-ttu-id="a8c36-122">O fragmento de código a seguir usa o [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) objeto chamado `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="a8c36-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="a8c36-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8c36-123">Requirements</span></span>  
 <span data-ttu-id="a8c36-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c36-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c36-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8c36-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8c36-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8c36-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8c36-127">**Versões do .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c36-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c36-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8c36-128">See Also</span></span>  
 [<span data-ttu-id="a8c36-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a8c36-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a8c36-130">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="a8c36-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
