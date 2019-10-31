---
title: Interface ISymUnmanagedAsyncMethod
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 0b8adba9dbffbdc47bb526cef9aad3ffa4b48065
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129219"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="b99bf-102">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="b99bf-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="b99bf-103">Essa interface é o complemento de leitura para a [interface ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b99bf-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b99bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b99bf-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="b99bf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b99bf-105">Methods</span></span>  
 <span data-ttu-id="b99bf-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="b99bf-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="b99bf-107">Método</span><span class="sxs-lookup"><span data-stu-id="b99bf-107">Method</span></span>|<span data-ttu-id="b99bf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b99bf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b99bf-109">Método GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="b99bf-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="b99bf-110">Consulte o [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="b99bf-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="b99bf-111">Método GetAsyncStepInfoCount</span><span class="sxs-lookup"><span data-stu-id="b99bf-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="b99bf-112">Consulte o [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="b99bf-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="b99bf-113">Método GetCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="b99bf-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="b99bf-114">Consulte o [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="b99bf-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="b99bf-115">Método GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="b99bf-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="b99bf-116">Consulte o [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="b99bf-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="b99bf-117">Método HasCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="b99bf-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="b99bf-118">Consulte o [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="b99bf-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="b99bf-119">Método IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="b99bf-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="b99bf-120">Verifica se o método tem informações assíncronas ou não.</span><span class="sxs-lookup"><span data-stu-id="b99bf-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="b99bf-121">Se esse método retornar `FALSE`, ele não será válido para chamar outros métodos nesta interface.</span><span class="sxs-lookup"><span data-stu-id="b99bf-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="b99bf-122">Eles serão retornados `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="b99bf-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b99bf-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b99bf-123">Requirements</span></span>  
 <span data-ttu-id="b99bf-124">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b99bf-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99bf-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b99bf-125">See also</span></span>

- [<span data-ttu-id="b99bf-126">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b99bf-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
