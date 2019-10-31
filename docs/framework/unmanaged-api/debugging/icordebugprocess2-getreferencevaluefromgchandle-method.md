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
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137215"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="87b44-102">Método ICorDebugProcess2::GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="87b44-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="87b44-103">Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="87b44-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87b44-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87b44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87b44-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="87b44-106">no Um ponteiro para um objeto gerenciado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="87b44-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="87b44-107">Esse valor é um objeto <xref:System.IntPtr> e pode ser recuperado do <xref:System.Runtime.InteropServices.GCHandle> para o objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="87b44-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="87b44-108">fora Um ponteiro para o endereço de um objeto ICorDebugReferenceValue que representa uma referência ao objeto gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="87b44-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87b44-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="87b44-109">Remarks</span></span>  
 <span data-ttu-id="87b44-110">Não confunda o valor de referência retornado com um valor de referência de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="87b44-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="87b44-111">A referência retornada se comporta como uma referência normal.</span><span class="sxs-lookup"><span data-stu-id="87b44-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="87b44-112">Ele é desabilitado quando a execução do código continua após um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="87b44-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="87b44-113">O tempo de vida do objeto de destino não é afetado pelo tempo de vida do valor de referência.</span><span class="sxs-lookup"><span data-stu-id="87b44-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87b44-114">O método `GetReferenceValueFromGCHandle` não valida o identificador.</span><span class="sxs-lookup"><span data-stu-id="87b44-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="87b44-115">Portanto, o método `GetReferenceValueFromGCHandle` pode potencialmente corromper o depurador e o código que está sendo depurado se um identificador inválido for passado.</span><span class="sxs-lookup"><span data-stu-id="87b44-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87b44-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87b44-116">Requirements</span></span>  
 <span data-ttu-id="87b44-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87b44-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87b44-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87b44-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87b44-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87b44-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87b44-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87b44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
