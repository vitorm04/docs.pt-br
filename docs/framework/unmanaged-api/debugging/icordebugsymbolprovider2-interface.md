---
title: Interface ICorDebugSymbolProvider2
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587fc29edce72edca7c811c737d67d96b7cafd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955466"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="1af6f-102">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="1af6f-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="1af6f-103">Estende logicamente a interface [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) para recuperar informações adicionais de símbolo de depuração.</span><span class="sxs-lookup"><span data-stu-id="1af6f-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1af6f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1af6f-104">Methods</span></span>  
  
|<span data-ttu-id="1af6f-105">Método</span><span class="sxs-lookup"><span data-stu-id="1af6f-105">Method</span></span>|<span data-ttu-id="1af6f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1af6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1af6f-107">Método GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="1af6f-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="1af6f-108">Retorna o método iniciando o endereço virtual relativo de um método e o quadro pai, dado um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="1af6f-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="1af6f-109">Método GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="1af6f-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="1af6f-110">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="1af6f-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1af6f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1af6f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1af6f-112">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1af6f-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1af6f-113">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="1af6f-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1af6f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1af6f-114">Requirements</span></span>  
 <span data-ttu-id="1af6f-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af6f-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1af6f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1af6f-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1af6f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1af6f-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af6f-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af6f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1af6f-119">See also</span></span>

- [<span data-ttu-id="1af6f-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="1af6f-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1af6f-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1af6f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1af6f-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="1af6f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
