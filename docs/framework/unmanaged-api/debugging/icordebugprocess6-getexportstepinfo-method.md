---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d0758a8603b7c31844b39c9f3beefea04e0a029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422953"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="c71cc-102">Método ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="c71cc-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="c71cc-103">Fornece informações sobre funções exportadas de tempo de execução para ajudar a percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c71cc-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c71cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c71cc-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c71cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c71cc-105">Parameters</span></span>  
 <span data-ttu-id="c71cc-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="c71cc-106">pszExportName</span></span>  
 <span data-ttu-id="c71cc-107">[in] O nome de uma função de exportação de tempo de execução gravada na tabela de exportação PE.</span><span class="sxs-lookup"><span data-stu-id="c71cc-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="c71cc-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="c71cc-108">invokeKind</span></span>  
 <span data-ttu-id="c71cc-109">[out] Um ponteiro para membro de [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeração que descreve como a função exportada invocará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c71cc-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="c71cc-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="c71cc-110">invokePurpose</span></span>  
 <span data-ttu-id="c71cc-111">[out] Um ponteiro para membro de [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeração que descreve o motivo pelo qual a função exportada chamará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c71cc-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c71cc-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c71cc-112">Return Value</span></span>  
 <span data-ttu-id="c71cc-113">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c71cc-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="c71cc-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c71cc-114">Return value</span></span>|<span data-ttu-id="c71cc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c71cc-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="c71cc-116">A chamada de método foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c71cc-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="c71cc-117">`pInvokeKind` ou `pInvokePurpose` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="c71cc-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="c71cc-118">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="c71cc-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="c71cc-119">Conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c71cc-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c71cc-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="c71cc-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c71cc-121">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c71cc-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c71cc-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c71cc-122">Requirements</span></span>  
 <span data-ttu-id="c71cc-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c71cc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c71cc-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c71cc-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c71cc-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c71cc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c71cc-126">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c71cc-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71cc-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c71cc-127">See Also</span></span>  
 [<span data-ttu-id="c71cc-128">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="c71cc-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="c71cc-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c71cc-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
