---
title: "Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="1d282-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="1d282-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="1d282-103">Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.</span><span class="sxs-lookup"><span data-stu-id="1d282-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="1d282-104">O deslocamento de IL de catch gerado é usado pelo depurador para tratar o problema como se fosse código não-usuário, mesmo que isso pode ocorrer em um método de código do usuário.</span><span class="sxs-lookup"><span data-stu-id="1d282-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="1d282-105">Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="1d282-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d282-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d282-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d282-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d282-107">Parameters</span></span>  
  
|<span data-ttu-id="1d282-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="1d282-108">Parameter</span></span>|<span data-ttu-id="1d282-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d282-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="1d282-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1d282-110">Return Value</span></span>  
 <span data-ttu-id="1d282-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1d282-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d282-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d282-112">Requirements</span></span>  
 <span data-ttu-id="1d282-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1d282-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d282-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d282-114">See Also</span></span>  
 [<span data-ttu-id="1d282-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="1d282-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
