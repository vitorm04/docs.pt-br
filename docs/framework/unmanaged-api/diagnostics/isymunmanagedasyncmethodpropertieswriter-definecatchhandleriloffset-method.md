---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441767"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="65d24-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="65d24-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="65d24-103">Define o deslocamento de IL para o manipulador catch gerado pelo compilador que encapsula um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="65d24-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="65d24-104">O deslocamento de IL do catch gerado é usado pelo depurador para lidar com o Catch como se fosse um código não-usuário, embora possa ocorrer em um método de código de usuário.</span><span class="sxs-lookup"><span data-stu-id="65d24-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="65d24-105">Em particular, ele é usado em resposta a um evento de exceção **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="65d24-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d24-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65d24-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65d24-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65d24-107">Parameters</span></span>  
  
|<span data-ttu-id="65d24-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="65d24-108">Parameter</span></span>|<span data-ttu-id="65d24-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="65d24-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="65d24-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="65d24-110">Return Value</span></span>  
 <span data-ttu-id="65d24-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="65d24-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d24-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65d24-112">Requirements</span></span>  
 <span data-ttu-id="65d24-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="65d24-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d24-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="65d24-114">See also</span></span>

- [<span data-ttu-id="65d24-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="65d24-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
