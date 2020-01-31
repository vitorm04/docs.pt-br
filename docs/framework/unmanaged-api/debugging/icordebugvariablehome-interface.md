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
ms.openlocfilehash: c347346c9157fea843527c662e26ffcfba22ace4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790961"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="cc004-102">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="cc004-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="cc004-103">Representa uma variável local ou um argumento de uma função.</span><span class="sxs-lookup"><span data-stu-id="cc004-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc004-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cc004-104">Methods</span></span>  
  
|<span data-ttu-id="cc004-105">Método</span><span class="sxs-lookup"><span data-stu-id="cc004-105">Method</span></span>|<span data-ttu-id="cc004-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc004-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc004-107">Método GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="cc004-107">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="cc004-108">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="cc004-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="cc004-109">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="cc004-109">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="cc004-110">Obtém a instância "ICorDebugCode" que contém este objeto de `ICorDebugVariableHome`.</span><span class="sxs-lookup"><span data-stu-id="cc004-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="cc004-111">Método GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="cc004-111">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="cc004-112">Obtém o intervalo nativo no qual essa variável está ativa.</span><span class="sxs-lookup"><span data-stu-id="cc004-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="cc004-113">Método GetLocationType</span><span class="sxs-lookup"><span data-stu-id="cc004-113">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="cc004-114">Obtém o tipo do local nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="cc004-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="cc004-115">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="cc004-115">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="cc004-116">Obtém o deslocamento do registro base de uma variável.</span><span class="sxs-lookup"><span data-stu-id="cc004-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="cc004-117">Método GetRegister</span><span class="sxs-lookup"><span data-stu-id="cc004-117">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="cc004-118">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="cc004-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="cc004-119">Método GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="cc004-119">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="cc004-120">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="cc004-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cc004-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc004-121">Example</span></span>  
 <span data-ttu-id="cc004-122">O fragmento de código a seguir usa o objeto [ICorDebugCode4](icordebugcode4-interface.md) chamado `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="cc004-122">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="cc004-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cc004-123">Requirements</span></span>  
 <span data-ttu-id="cc004-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc004-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc004-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc004-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc004-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc004-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc004-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc004-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc004-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="cc004-128">See also</span></span>

- [<span data-ttu-id="cc004-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cc004-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cc004-130">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="cc004-130">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
