---
title: Interface ICorDebugSymbolProvider2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff0446ba8646620cb7322f74a81769e41f35b0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="dd70b-102">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="dd70b-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="dd70b-103">Logicamente estende o [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="dd70b-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd70b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="dd70b-104">Methods</span></span>  
  
|<span data-ttu-id="dd70b-105">Método</span><span class="sxs-lookup"><span data-stu-id="dd70b-105">Method</span></span>|<span data-ttu-id="dd70b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd70b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd70b-107">Método GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="dd70b-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="dd70b-108">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="dd70b-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="dd70b-109">Método GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="dd70b-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="dd70b-110">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="dd70b-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd70b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd70b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd70b-112">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dd70b-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="dd70b-113">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="dd70b-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd70b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd70b-114">Requirements</span></span>  
 <span data-ttu-id="dd70b-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd70b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd70b-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd70b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd70b-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd70b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd70b-118">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd70b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd70b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd70b-119">See Also</span></span>  
 [<span data-ttu-id="dd70b-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="dd70b-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="dd70b-121">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="dd70b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dd70b-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="dd70b-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
