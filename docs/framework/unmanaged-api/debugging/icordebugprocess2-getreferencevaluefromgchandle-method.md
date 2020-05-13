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
ms.openlocfilehash: 143eefd557511f80007c88c1678143a885377467
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212978"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="6097f-102">Método ICorDebugProcess2::GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="6097f-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="6097f-103">Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6097f-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6097f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6097f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6097f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6097f-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="6097f-106">no Um ponteiro para um objeto gerenciado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6097f-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="6097f-107">Esse valor é um <xref:System.IntPtr> objeto e pode ser recuperado do <xref:System.Runtime.InteropServices.GCHandle> para o objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6097f-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="6097f-108">fora Um ponteiro para o endereço de um objeto ICorDebugReferenceValue que representa uma referência ao objeto gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="6097f-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6097f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6097f-109">Remarks</span></span>  
 <span data-ttu-id="6097f-110">Não confunda o valor de referência retornado com um valor de referência de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6097f-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="6097f-111">A referência retornada se comporta como uma referência normal.</span><span class="sxs-lookup"><span data-stu-id="6097f-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="6097f-112">Ele é desabilitado quando a execução do código continua após um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="6097f-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="6097f-113">O tempo de vida do objeto de destino não é afetado pelo tempo de vida do valor de referência.</span><span class="sxs-lookup"><span data-stu-id="6097f-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6097f-114">O `GetReferenceValueFromGCHandle` método não valida o identificador.</span><span class="sxs-lookup"><span data-stu-id="6097f-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="6097f-115">Portanto, o `GetReferenceValueFromGCHandle` método pode potencialmente corromper o depurador e o código que está sendo depurado se um identificador inválido for passado.</span><span class="sxs-lookup"><span data-stu-id="6097f-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6097f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6097f-116">Requirements</span></span>  
 <span data-ttu-id="6097f-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6097f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6097f-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6097f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6097f-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6097f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6097f-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6097f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
