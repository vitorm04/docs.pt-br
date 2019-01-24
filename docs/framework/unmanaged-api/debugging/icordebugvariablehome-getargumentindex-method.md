---
title: Método ICorDebugVariableHome::GetArgumentIndex
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 163704bf9a71ceda04bdfd73f9ca676c19d8a62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526634"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="84469-102">Método ICorDebugVariableHome::GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="84469-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="84469-103">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="84469-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84469-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84469-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84469-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84469-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="84469-106">[out] Um ponteiro para o índice do argumento.</span><span class="sxs-lookup"><span data-stu-id="84469-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84469-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="84469-107">Return Value</span></span>  
 <span data-ttu-id="84469-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="84469-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="84469-109">Valor</span><span class="sxs-lookup"><span data-stu-id="84469-109">Value</span></span>|<span data-ttu-id="84469-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="84469-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="84469-111">A chamada de método retornou um índice de argumento válido.</span><span class="sxs-lookup"><span data-stu-id="84469-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="84469-112">O atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa uma variável local.</span><span class="sxs-lookup"><span data-stu-id="84469-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84469-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="84469-113">Remarks</span></span>  
 <span data-ttu-id="84469-114">O índice do argumento pode ser usado para recuperar metadados para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="84469-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84469-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84469-115">Requirements</span></span>  
 <span data-ttu-id="84469-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84469-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84469-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84469-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84469-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84469-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84469-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84469-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84469-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84469-120">See also</span></span>
- [<span data-ttu-id="84469-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="84469-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
