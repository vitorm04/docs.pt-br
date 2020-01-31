---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 118f52db63464b4c9355ba9ee7f330b996c5bf71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792242"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="c963f-102">Método ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="c963f-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="c963f-103">Fornece informações sobre funções exportadas de runtime para ajudar a percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c963f-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c963f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c963f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c963f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c963f-105">Parameters</span></span>  
 <span data-ttu-id="c963f-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="c963f-106">pszExportName</span></span>  
 <span data-ttu-id="c963f-107">[in] O nome de uma função de exportação de runtime gravada na tabela de exportação PE.</span><span class="sxs-lookup"><span data-stu-id="c963f-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="c963f-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="c963f-108">invokeKind</span></span>  
 <span data-ttu-id="c963f-109">fora Um ponteiro para um membro da enumeração [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) que descreve como a função exportada invocará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c963f-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="c963f-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="c963f-110">invokePurpose</span></span>  
 <span data-ttu-id="c963f-111">fora Um ponteiro para um membro da enumeração [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) que descreve por que a função exportada chamará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c963f-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c963f-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c963f-112">Return Value</span></span>  
 <span data-ttu-id="c963f-113">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c963f-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="c963f-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c963f-114">Return value</span></span>|<span data-ttu-id="c963f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c963f-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="c963f-116">A chamada de método foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c963f-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="c963f-117">`pInvokeKind` ou `pInvokePurpose` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="c963f-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="c963f-118">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="c963f-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="c963f-119">Conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c963f-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c963f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="c963f-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c963f-121">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c963f-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c963f-122">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c963f-122">Requirements</span></span>  
 <span data-ttu-id="c963f-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c963f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c963f-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c963f-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c963f-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c963f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c963f-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c963f-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c963f-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="c963f-127">See also</span></span>

- [<span data-ttu-id="c963f-128">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="c963f-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="c963f-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c963f-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
