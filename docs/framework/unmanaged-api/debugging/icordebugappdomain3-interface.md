---
title: Interface ICorDebugAppDomain3
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c141ca9a8e1c74015883f45cb2eaa9183bb3d89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177522"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="c713f-102">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="c713f-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="c713f-103">Fornece métodos para recuperar informações sobre as representações gerenciadas de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos carregados atualmente em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c713f-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="c713f-104">Essa interface é uma extensão das interfaces ICorDebugAppDomain e ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="c713f-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c713f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c713f-105">Methods</span></span>  
  
|<span data-ttu-id="c713f-106">Método</span><span class="sxs-lookup"><span data-stu-id="c713f-106">Method</span></span>|<span data-ttu-id="c713f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c713f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c713f-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="c713f-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="c713f-109">Obtém um enumerador para todos os armazenados em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos.</span><span class="sxs-lookup"><span data-stu-id="c713f-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="c713f-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="c713f-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="c713f-111">Obtém um enumerador para armazenada em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="c713f-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c713f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c713f-112">Remarks</span></span>  
 <span data-ttu-id="c713f-113">Essa interface destina-se a ser usado por um depurador em conjunto com uma chamada de função de avaliação para `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="c713f-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="c713f-114">Quando o método recupera os identificadores de interface com suporte por um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objeto de servidor, o depurador pode usar os métodos definidos nessa interface mapeá-los para os tipos gerenciados que correspondem a essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="c713f-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="c713f-115">Para recuperar uma instância dessa interface, execute `QueryInterface` em uma instância da interface ICorDebugAppDomain ou ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="c713f-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c713f-116">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c713f-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c713f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c713f-117">Requirements</span></span>  
 **<span data-ttu-id="c713f-118">Plataformas:</span><span class="sxs-lookup"><span data-stu-id="c713f-118">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="c713f-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c713f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c713f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c713f-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c713f-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c713f-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c713f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c713f-122">See also</span></span>

- [<span data-ttu-id="c713f-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c713f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
