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
ms.openlocfilehash: 21da325ee58df65ac449464f8292f2ba94d99338
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943290"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="e4aa9-102">Método ICorDebugProcess2::GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="e4aa9-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="e4aa9-103">Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4aa9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4aa9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4aa9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4aa9-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="e4aa9-106">no Um ponteiro para um objeto gerenciado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="e4aa9-107">Esse valor é um <xref:System.IntPtr> objeto e pode ser recuperado <xref:System.Runtime.InteropServices.GCHandle> do para o objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="e4aa9-108">fora Um ponteiro para o endereço de um objeto ICorDebugReferenceValue que representa uma referência ao objeto gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4aa9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4aa9-109">Remarks</span></span>  
 <span data-ttu-id="e4aa9-110">Não confunda o valor de referência retornado com um valor de referência de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="e4aa9-111">A referência retornada se comporta como uma referência normal.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="e4aa9-112">Ele é desabilitado quando a execução do código continua após um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="e4aa9-113">O tempo de vida do objeto de destino não é afetado pelo tempo de vida do valor de referência.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4aa9-114">O `GetReferenceValueFromGCHandle` método não valida o identificador.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="e4aa9-115">Portanto, o `GetReferenceValueFromGCHandle` método pode potencialmente corromper o depurador e o código que está sendo depurado se um identificador inválido for passado.</span><span class="sxs-lookup"><span data-stu-id="e4aa9-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4aa9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4aa9-116">Requirements</span></span>  
 <span data-ttu-id="e4aa9-117">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4aa9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4aa9-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4aa9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4aa9-119">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4aa9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4aa9-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4aa9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
