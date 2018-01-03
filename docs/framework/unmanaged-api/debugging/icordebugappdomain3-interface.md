---
title: Interface ICorDebugAppDomain3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3
helpviewer_keywords: ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 017a2f018569b17c0b0011638e16f1921b6c9801
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="4b106-102">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="4b106-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="4b106-103">Fornece métodos para recuperar informações sobre as representações gerenciadas de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos atualmente carregados em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4b106-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="4b106-104">Essa interface é uma extensão das interfaces ICorDebugAppDomain e ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="4b106-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b106-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4b106-105">Methods</span></span>  
  
|<span data-ttu-id="4b106-106">Método</span><span class="sxs-lookup"><span data-stu-id="4b106-106">Method</span></span>|<span data-ttu-id="4b106-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b106-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b106-108">Icordebugappdomain3</span><span class="sxs-lookup"><span data-stu-id="4b106-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="4b106-109">Obtém um enumerador para todos armazenados em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos.</span><span class="sxs-lookup"><span data-stu-id="4b106-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="4b106-110">Icordebugappdomain3</span><span class="sxs-lookup"><span data-stu-id="4b106-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="4b106-111">Obtém um enumerador para armazenada em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="4b106-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b106-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b106-112">Remarks</span></span>  
 <span data-ttu-id="4b106-113">Essa interface destina-se a ser usado por um depurador em conjunto com uma chamada de função de avaliação para `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="4b106-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="4b106-114">Quando o método recupera os identificadores de interface com suporte por um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objeto de servidor, o depurador pode usar os métodos definidos nessa interface mapeá-los para os tipos gerenciados que correspondem a essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="4b106-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="4b106-115">Para recuperar uma instância desta interface, executar `QueryInterface` em uma instância da interface ICorDebugAppDomain ou ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="4b106-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b106-116">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="4b106-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b106-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b106-117">Requirements</span></span>  
 <span data-ttu-id="4b106-118">**Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b106-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="4b106-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b106-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b106-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b106-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b106-121">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b106-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b106-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b106-122">See Also</span></span>  
 [<span data-ttu-id="4b106-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4b106-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
