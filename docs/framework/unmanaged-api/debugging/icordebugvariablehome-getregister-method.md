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
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790983"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="14bcc-102">Método ICorDebugVariableHome:: getregister</span><span class="sxs-lookup"><span data-stu-id="14bcc-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="14bcc-103">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="14bcc-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bcc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14bcc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14bcc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14bcc-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="14bcc-106">fora Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="14bcc-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14bcc-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="14bcc-107">Return Value</span></span>  
 <span data-ttu-id="14bcc-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="14bcc-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="14bcc-109">Value</span><span class="sxs-lookup"><span data-stu-id="14bcc-109">Value</span></span>|<span data-ttu-id="14bcc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="14bcc-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="14bcc-111">A variável está no registro indicado pelo argumento `pRegister`.</span><span class="sxs-lookup"><span data-stu-id="14bcc-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="14bcc-112">A variável não está em um local de registro ou relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="14bcc-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14bcc-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="14bcc-113">Requirements</span></span>  
 <span data-ttu-id="14bcc-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14bcc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14bcc-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14bcc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14bcc-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14bcc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14bcc-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14bcc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bcc-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="14bcc-118">See also</span></span>

- [<span data-ttu-id="14bcc-119">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="14bcc-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="14bcc-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="14bcc-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
