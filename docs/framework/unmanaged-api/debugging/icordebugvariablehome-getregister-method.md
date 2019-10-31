---
title: 'Método ICorDebugVariableHome:: getregister'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 4c9932c3eeebd0101ee364c9b4d0b0a26862c4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125068"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="1c4a1-102">Método ICorDebugVariableHome:: getregister</span><span class="sxs-lookup"><span data-stu-id="1c4a1-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="1c4a1-103">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="1c4a1-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c4a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c4a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c4a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c4a1-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="1c4a1-106">fora Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="1c4a1-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c4a1-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1c4a1-107">Return Value</span></span>  
 <span data-ttu-id="1c4a1-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="1c4a1-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="1c4a1-109">Valor</span><span class="sxs-lookup"><span data-stu-id="1c4a1-109">Value</span></span>|<span data-ttu-id="1c4a1-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c4a1-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1c4a1-111">A variável está no registro indicado pelo argumento `pRegister`.</span><span class="sxs-lookup"><span data-stu-id="1c4a1-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1c4a1-112">A variável não está em um local de registro ou relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="1c4a1-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c4a1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c4a1-113">Requirements</span></span>  
 <span data-ttu-id="1c4a1-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c4a1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c4a1-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c4a1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c4a1-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c4a1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c4a1-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c4a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4a1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c4a1-118">See also</span></span>

- [<span data-ttu-id="1c4a1-119">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="1c4a1-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="1c4a1-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="1c4a1-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
