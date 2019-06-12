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
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025884"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="9733e-102">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="9733e-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="9733e-103">Fornece métodos para recuperar informações sobre as representações gerenciadas dos tipos de tempo de execução do Windows atualmente carregados em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9733e-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="9733e-104">Essa interface é uma extensão das interfaces ICorDebugAppDomain e ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="9733e-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9733e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9733e-105">Methods</span></span>  
  
|<span data-ttu-id="9733e-106">Método</span><span class="sxs-lookup"><span data-stu-id="9733e-106">Method</span></span>|<span data-ttu-id="9733e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9733e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9733e-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="9733e-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="9733e-109">Obtém um enumerador para todos os tipos de tempo de execução do Windows em cache.</span><span class="sxs-lookup"><span data-stu-id="9733e-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="9733e-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="9733e-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="9733e-111">Obtém um enumerador para os tipos de tempo de execução do Windows em cache em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="9733e-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9733e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9733e-112">Remarks</span></span>  
 <span data-ttu-id="9733e-113">Essa interface destina-se a ser usado por um depurador em conjunto com uma chamada de função de avaliação para `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="9733e-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="9733e-114">Quando o método recupera os identificadores de interface com suporte por um objeto de servidor de tempo de execução do Windows, o depurador pode usar os métodos definidos nessa interface mapeá-los para os tipos gerenciados que correspondem a essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="9733e-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="9733e-115">Para recuperar uma instância dessa interface, execute `QueryInterface` em uma instância da interface ICorDebugAppDomain ou ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="9733e-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9733e-116">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="9733e-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9733e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9733e-117">Requirements</span></span>  
 <span data-ttu-id="9733e-118">**Plataformas:** Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="9733e-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="9733e-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9733e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9733e-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9733e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9733e-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9733e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9733e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9733e-122">See also</span></span>

- [<span data-ttu-id="9733e-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9733e-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
