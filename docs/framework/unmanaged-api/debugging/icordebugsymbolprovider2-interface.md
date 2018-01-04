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
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="29abc-102">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="29abc-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="29abc-103">Logicamente estende o [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="29abc-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29abc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="29abc-104">Methods</span></span>  
  
|<span data-ttu-id="29abc-105">Método</span><span class="sxs-lookup"><span data-stu-id="29abc-105">Method</span></span>|<span data-ttu-id="29abc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="29abc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29abc-107">Método GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="29abc-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="29abc-108">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="29abc-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="29abc-109">Método GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="29abc-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="29abc-110">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="29abc-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29abc-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="29abc-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29abc-112">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="29abc-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="29abc-113">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="29abc-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29abc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29abc-114">Requirements</span></span>  
 <span data-ttu-id="29abc-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29abc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29abc-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29abc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29abc-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29abc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29abc-118">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29abc-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29abc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29abc-119">See Also</span></span>  
 [<span data-ttu-id="29abc-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="29abc-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="29abc-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="29abc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="29abc-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="29abc-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
