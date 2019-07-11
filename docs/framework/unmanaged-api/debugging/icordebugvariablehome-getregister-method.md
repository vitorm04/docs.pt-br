---
title: Método ICorDebugVariableHome::GetRegister
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b3b80546095b79dc5b551a9c5e92ec15c0dddb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771793"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="c7f3e-102">Método ICorDebugVariableHome::GetRegister</span><span class="sxs-lookup"><span data-stu-id="c7f3e-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="c7f3e-103">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="c7f3e-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7f3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7f3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7f3e-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="c7f3e-106">[out] Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="c7f3e-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7f3e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c7f3e-107">Return Value</span></span>  
 <span data-ttu-id="c7f3e-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c7f3e-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="c7f3e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="c7f3e-109">Value</span></span>|<span data-ttu-id="c7f3e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7f3e-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="c7f3e-111">A variável está no registro, indicado pelo `pRegister` argumento.</span><span class="sxs-lookup"><span data-stu-id="c7f3e-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="c7f3e-112">A variável não está em um registro ou em um local relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="c7f3e-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7f3e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7f3e-113">Requirements</span></span>  
 <span data-ttu-id="c7f3e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7f3e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7f3e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7f3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7f3e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7f3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7f3e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7f3e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f3e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7f3e-118">See also</span></span>

- [<span data-ttu-id="c7f3e-119">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="c7f3e-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="c7f3e-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="c7f3e-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
