---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137209"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="c7c5f-102">Método ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="c7c5f-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="c7c5f-103">Fornece informações sobre funções exportadas de tempo de execução para ajudar a percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7c5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7c5f-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7c5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7c5f-105">Parameters</span></span>  
 <span data-ttu-id="c7c5f-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="c7c5f-106">pszExportName</span></span>  
 <span data-ttu-id="c7c5f-107">[in] O nome de uma função de exportação de tempo de execução gravada na tabela de exportação PE.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="c7c5f-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="c7c5f-108">invokeKind</span></span>  
 <span data-ttu-id="c7c5f-109">[out] Um ponteiro para um membro do [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeração que descreve como a função exportada invocará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="c7c5f-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="c7c5f-110">invokePurpose</span></span>  
 <span data-ttu-id="c7c5f-111">[out] Um ponteiro para um membro do [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeração que descreve por que a função exportada chamará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7c5f-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c7c5f-112">Return Value</span></span>  
 <span data-ttu-id="c7c5f-113">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="c7c5f-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c7c5f-114">Return value</span></span>|<span data-ttu-id="c7c5f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7c5f-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="c7c5f-116">A chamada de método foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="c7c5f-117">`pInvokeKind` ou `pInvokePurpose` está **nulo**.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="c7c5f-118">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="c7c5f-119">Conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7c5f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7c5f-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7c5f-121">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c7c5f-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7c5f-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7c5f-122">Requirements</span></span>  
 <span data-ttu-id="c7c5f-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7c5f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7c5f-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7c5f-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7c5f-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7c5f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7c5f-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7c5f-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c5f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7c5f-127">See also</span></span>

- [<span data-ttu-id="c7c5f-128">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="c7c5f-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="c7c5f-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c7c5f-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
