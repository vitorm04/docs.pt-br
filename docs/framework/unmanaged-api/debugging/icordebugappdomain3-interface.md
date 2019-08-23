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
ms.openlocfilehash: c3676cb32ceaf6f241672751f0feafbd3cb83e05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968871"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="e4784-102">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="e4784-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="e4784-103">Fornece métodos para recuperar informações sobre as representações gerenciadas dos tipos de Windows Runtime atualmente carregados em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4784-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="e4784-104">Essa interface é uma extensão das interfaces ICorDebugAppDomain e ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="e4784-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4784-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e4784-105">Methods</span></span>  
  
|<span data-ttu-id="e4784-106">Método</span><span class="sxs-lookup"><span data-stu-id="e4784-106">Method</span></span>|<span data-ttu-id="e4784-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4784-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4784-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="e4784-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="e4784-109">Obtém um enumerador para todos os tipos de Windows Runtime em cache.</span><span class="sxs-lookup"><span data-stu-id="e4784-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="e4784-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="e4784-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="e4784-111">Obtém um enumerador para tipos de Windows Runtime em cache em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="e4784-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4784-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4784-112">Remarks</span></span>  
 <span data-ttu-id="e4784-113">Essa interface deve ser usada por um depurador em conjunto com uma chamada de avaliação de função para `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="e4784-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="e4784-114">Quando o método recupera os identificadores de interface com suporte de um objeto de servidor Windows Runtime, o depurador pode usar os métodos definidos nesta interface para mapeá-los para tipos gerenciados que correspondem a essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="e4784-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="e4784-115">Para recuperar uma instância dessa interface, execute `QueryInterface` em uma instância da interface ICorDebugAppDomain ou ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="e4784-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4784-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="e4784-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4784-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4784-117">Requirements</span></span>  
 <span data-ttu-id="e4784-118">**Compatíveis** Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="e4784-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="e4784-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4784-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4784-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4784-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4784-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4784-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4784-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4784-122">See also</span></span>

- [<span data-ttu-id="e4784-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e4784-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
