---
title: Método ICorDebugProcess2::GetReferenceValueFromGCHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60624a5f6323399d06bda4e0280de8fbe861bd9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="d0ba2-102">Método ICorDebugProcess2::GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="d0ba2-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="d0ba2-103">Obtém um ponteiro de referência para o objeto especificado gerenciado que possua uma coleta de lixo a alça.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ba2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0ba2-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0ba2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0ba2-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="d0ba2-106">[in] Um ponteiro para um objeto gerenciado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="d0ba2-107">Esse valor é um <xref:System.IntPtr> de objeto e podem ser recuperados do <xref:System.Runtime.InteropServices.GCHandle> para o objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="d0ba2-108">[out] Um ponteiro para o endereço de um objeto ICorDebugReferenceValue que representa uma referência ao objeto gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0ba2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0ba2-109">Remarks</span></span>  
 <span data-ttu-id="d0ba2-110">Não confunda o valor de referência fornecida com um valor de referência de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="d0ba2-111">A referência retornada se comporta como uma referência normal.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="d0ba2-112">Ele é desabilitado quando a execução de código continua depois de um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="d0ba2-113">O tempo de vida do objeto de destino não é afetado pelo tempo de vida do valor de referência.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0ba2-114">O `GetReferenceValueFromGCHandle` método não valida o identificador.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="d0ba2-115">Portanto, o `GetReferenceValueFromGCHandle` método pode corromper o depurador e o código que está sendo depurado se um identificador inválido for passado.</span><span class="sxs-lookup"><span data-stu-id="d0ba2-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ba2-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0ba2-116">Requirements</span></span>  
 <span data-ttu-id="d0ba2-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0ba2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ba2-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0ba2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0ba2-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0ba2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0ba2-120">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ba2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
