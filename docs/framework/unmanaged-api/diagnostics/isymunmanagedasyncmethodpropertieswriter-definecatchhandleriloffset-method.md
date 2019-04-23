---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196743"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="dac6c-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="dac6c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="dac6c-103">Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.</span><span class="sxs-lookup"><span data-stu-id="dac6c-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="dac6c-104">O deslocamento de IL de catch gerado é usado pelo depurador para tratar o problema como se fosse o código de não usuário, mesmo que ele pode ocorrer em um método de código do usuário.</span><span class="sxs-lookup"><span data-stu-id="dac6c-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="dac6c-105">Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="dac6c-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac6c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dac6c-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac6c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dac6c-107">Parameters</span></span>  
  
|<span data-ttu-id="dac6c-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="dac6c-108">Parameter</span></span>|<span data-ttu-id="dac6c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dac6c-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="dac6c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dac6c-110">Return Value</span></span>  
 <span data-ttu-id="dac6c-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="dac6c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac6c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dac6c-112">Requirements</span></span>  
 <span data-ttu-id="dac6c-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dac6c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac6c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dac6c-114">See also</span></span>

- [<span data-ttu-id="dac6c-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="dac6c-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
