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
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396827"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="65b49-102">Método ICorDebugVariableHome:: getregister</span><span class="sxs-lookup"><span data-stu-id="65b49-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="65b49-103">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER` e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="65b49-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65b49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65b49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65b49-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="65b49-106">fora Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER` e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="65b49-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65b49-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="65b49-107">Return Value</span></span>  
 <span data-ttu-id="65b49-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="65b49-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="65b49-109">Valor</span><span class="sxs-lookup"><span data-stu-id="65b49-109">Value</span></span>|<span data-ttu-id="65b49-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="65b49-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="65b49-111">A variável está no registro indicado pelo `pRegister` argumento.</span><span class="sxs-lookup"><span data-stu-id="65b49-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="65b49-112">A variável não está em um local de registro ou relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="65b49-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65b49-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65b49-113">Requirements</span></span>  
 <span data-ttu-id="65b49-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b49-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b49-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65b49-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65b49-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65b49-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65b49-117">**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b49-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b49-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="65b49-118">See also</span></span>

- [<span data-ttu-id="65b49-119">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="65b49-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="65b49-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="65b49-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
