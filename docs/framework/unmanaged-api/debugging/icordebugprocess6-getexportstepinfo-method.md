---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948611"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="da1a6-102">Método ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="da1a6-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="da1a6-103">Fornece informações sobre funções exportadas de tempo de execução para ajudar a percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="da1a6-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da1a6-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da1a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da1a6-105">Parameters</span></span>  
 <span data-ttu-id="da1a6-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="da1a6-106">pszExportName</span></span>  
 <span data-ttu-id="da1a6-107">[in] O nome de uma função de exportação de tempo de execução gravada na tabela de exportação PE.</span><span class="sxs-lookup"><span data-stu-id="da1a6-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="da1a6-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="da1a6-108">invokeKind</span></span>  
 <span data-ttu-id="da1a6-109">[out] Um ponteiro para um membro do [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeração que descreve como a função exportada invocará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="da1a6-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="da1a6-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="da1a6-110">invokePurpose</span></span>  
 <span data-ttu-id="da1a6-111">[out] Um ponteiro para um membro do [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeração que descreve por que a função exportada chamará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="da1a6-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da1a6-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="da1a6-112">Return Value</span></span>  
 <span data-ttu-id="da1a6-113">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="da1a6-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="da1a6-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="da1a6-114">Return value</span></span>|<span data-ttu-id="da1a6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="da1a6-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="da1a6-116">A chamada de método foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="da1a6-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="da1a6-117">`pInvokeKind` ou `pInvokePurpose` está **nulo**.</span><span class="sxs-lookup"><span data-stu-id="da1a6-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="da1a6-118">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="da1a6-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="da1a6-119">Conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="da1a6-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da1a6-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="da1a6-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da1a6-121">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da1a6-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da1a6-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da1a6-122">Requirements</span></span>  
 <span data-ttu-id="da1a6-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da1a6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da1a6-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da1a6-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da1a6-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da1a6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da1a6-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da1a6-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1a6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da1a6-127">See also</span></span>

- [<span data-ttu-id="da1a6-128">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="da1a6-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="da1a6-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="da1a6-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
