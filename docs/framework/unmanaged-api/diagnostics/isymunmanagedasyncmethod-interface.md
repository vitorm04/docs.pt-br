---
title: Interface ISymUnmanagedAsyncMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f83723b59f525c06f04b7edeeae953dbf94556
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="63735-102">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="63735-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="63735-103">Essa interface é o complemento de leitura para [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="63735-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63735-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63735-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="63735-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="63735-105">Methods</span></span>  
 <span data-ttu-id="63735-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="63735-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="63735-107">Método</span><span class="sxs-lookup"><span data-stu-id="63735-107">Method</span></span>|<span data-ttu-id="63735-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="63735-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63735-109">Método GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="63735-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="63735-110">Consulte [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="63735-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="63735-111">Método GetAsyncStepInfoCount</span><span class="sxs-lookup"><span data-stu-id="63735-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="63735-112">Consulte [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="63735-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="63735-113">Método GetCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="63735-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="63735-114">Consulte [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="63735-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="63735-115">Método GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="63735-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="63735-116">Consulte [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="63735-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="63735-117">Método HasCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="63735-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="63735-118">Consulte [método DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="63735-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="63735-119">Método IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="63735-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="63735-120">Verifica se o método tem informações assíncrono ou não.</span><span class="sxs-lookup"><span data-stu-id="63735-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="63735-121">Se esse método retornar `FALSE` é inválido chamar outros métodos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="63735-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="63735-122">Eles serão retornar todos os `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="63735-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63735-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63735-123">Requirements</span></span>  
 <span data-ttu-id="63735-124">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="63735-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63735-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63735-125">See Also</span></span>  
 [<span data-ttu-id="63735-126">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="63735-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
