---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55d35db387d6184f68ff31a74253d3d1610c806f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741224"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="d82c8-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="d82c8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="d82c8-103">Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.</span><span class="sxs-lookup"><span data-stu-id="d82c8-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="d82c8-104">O deslocamento de IL de catch gerado é usado pelo depurador para tratar o problema como se fosse o código de não usuário, mesmo que ele pode ocorrer em um método de código do usuário.</span><span class="sxs-lookup"><span data-stu-id="d82c8-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="d82c8-105">Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="d82c8-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82c8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d82c8-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d82c8-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d82c8-107">Parameters</span></span>  
  
|<span data-ttu-id="d82c8-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d82c8-108">Parameter</span></span>|<span data-ttu-id="d82c8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d82c8-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="d82c8-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d82c8-110">Return Value</span></span>  
 <span data-ttu-id="d82c8-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d82c8-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82c8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d82c8-112">Requirements</span></span>  
 <span data-ttu-id="d82c8-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d82c8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82c8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d82c8-114">See also</span></span>
- [<span data-ttu-id="d82c8-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="d82c8-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
