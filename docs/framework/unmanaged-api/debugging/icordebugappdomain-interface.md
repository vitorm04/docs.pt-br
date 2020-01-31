---
title: Método ICorDebugAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785038"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="01e26-102">Método ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="01e26-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="01e26-103">Fornece métodos para depurar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="01e26-104">Essa interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="01e26-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01e26-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="01e26-105">Methods</span></span>  
  
|<span data-ttu-id="01e26-106">Método</span><span class="sxs-lookup"><span data-stu-id="01e26-106">Method</span></span>|<span data-ttu-id="01e26-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="01e26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01e26-108">Método Attach</span><span class="sxs-lookup"><span data-stu-id="01e26-108">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="01e26-109">Anexa o depurador ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="01e26-110">Método EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="01e26-110">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="01e26-111">Obtém um enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="01e26-112">Método EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="01e26-112">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="01e26-113">Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="01e26-114">Método EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="01e26-114">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="01e26-115">Obtém um enumerador para todos os percorridos ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="01e26-116">Método GetId</span><span class="sxs-lookup"><span data-stu-id="01e26-116">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="01e26-117">Obtém a ID exclusiva do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="01e26-118">Método GetModuleFromMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="01e26-118">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="01e26-119">Obtém o objeto ICorDebugModule com a interface de metadados fornecida.</span><span class="sxs-lookup"><span data-stu-id="01e26-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="01e26-120">Método GetName</span><span class="sxs-lookup"><span data-stu-id="01e26-120">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="01e26-121">Obtém o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="01e26-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="01e26-122">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="01e26-123">Obtém um ponteiro de interface para o domínio do aplicativo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="01e26-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="01e26-124">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="01e26-124">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="01e26-125">Obtém o processo que contém o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="01e26-126">Método IsAttached</span><span class="sxs-lookup"><span data-stu-id="01e26-126">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="01e26-127">Determina se o depurador está anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e26-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01e26-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="01e26-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01e26-129">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="01e26-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e26-130">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="01e26-130">Requirements</span></span>  
 <span data-ttu-id="01e26-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e26-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e26-132">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01e26-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01e26-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01e26-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01e26-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e26-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e26-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="01e26-135">See also</span></span>

- [<span data-ttu-id="01e26-136">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="01e26-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
