---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425425"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="5f13c-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="5f13c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="5f13c-103">Define o deslocamento para o manipulador catch gerado pelo compilador que encapsula um método assíncrono de IL.</span><span class="sxs-lookup"><span data-stu-id="5f13c-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="5f13c-104">O deslocamento de IL de catch gerado é usado pelo depurador para tratar o problema como se fosse código não-usuário, mesmo que isso pode ocorrer em um método de código do usuário.</span><span class="sxs-lookup"><span data-stu-id="5f13c-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="5f13c-105">Em particular, ele é usado em resposta a um **CatchHandlerFound** eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="5f13c-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f13c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f13c-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f13c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f13c-107">Parameters</span></span>  
  
|<span data-ttu-id="5f13c-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="5f13c-108">Parameter</span></span>|<span data-ttu-id="5f13c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f13c-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="5f13c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5f13c-110">Return Value</span></span>  
 <span data-ttu-id="5f13c-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5f13c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f13c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f13c-112">Requirements</span></span>  
 <span data-ttu-id="5f13c-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5f13c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f13c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f13c-114">See Also</span></span>  
 [<span data-ttu-id="5f13c-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="5f13c-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
