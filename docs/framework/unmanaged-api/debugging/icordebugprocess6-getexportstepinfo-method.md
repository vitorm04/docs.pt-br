---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: d92b05e3d84a230e87901378f34ed27ac38286b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123455"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="b2426-102">Método ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="b2426-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="b2426-103">Fornece informações sobre funções exportadas de runtime para ajudar a percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b2426-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2426-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2426-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2426-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2426-105">Parameters</span></span>  
 <span data-ttu-id="b2426-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="b2426-106">pszExportName</span></span>  
 <span data-ttu-id="b2426-107">[in] O nome de uma função de exportação de runtime gravada na tabela de exportação PE.</span><span class="sxs-lookup"><span data-stu-id="b2426-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="b2426-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="b2426-108">invokeKind</span></span>  
 <span data-ttu-id="b2426-109">fora Um ponteiro para um membro da enumeração [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) que descreve como a função exportada invocará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b2426-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="b2426-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="b2426-110">invokePurpose</span></span>  
 <span data-ttu-id="b2426-111">fora Um ponteiro para um membro da enumeração [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) que descreve por que a função exportada chamará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b2426-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2426-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b2426-112">Return Value</span></span>  
 <span data-ttu-id="b2426-113">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2426-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="b2426-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b2426-114">Return value</span></span>|<span data-ttu-id="b2426-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2426-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2426-116">A chamada de método foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b2426-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="b2426-117">`pInvokeKind` ou `pInvokePurpose` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="b2426-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="b2426-118">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="b2426-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="b2426-119">Conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="b2426-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2426-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2426-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2426-121">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b2426-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2426-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2426-122">Requirements</span></span>  
 <span data-ttu-id="b2426-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2426-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2426-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2426-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2426-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2426-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2426-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2426-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2426-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2426-127">See also</span></span>

- [<span data-ttu-id="b2426-128">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="b2426-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="b2426-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b2426-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
