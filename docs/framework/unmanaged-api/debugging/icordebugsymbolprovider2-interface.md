---
title: Interface ICorDebugSymbolProvider2
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea60ecd542300bf3833c4977b7f0910399a2e409
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504022"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="c383d-102">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="c383d-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="c383d-103">Estende logicamente a [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="c383d-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c383d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c383d-104">Methods</span></span>  
  
|<span data-ttu-id="c383d-105">Método</span><span class="sxs-lookup"><span data-stu-id="c383d-105">Method</span></span>|<span data-ttu-id="c383d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c383d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c383d-107">Método GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="c383d-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="c383d-108">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="c383d-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="c383d-109">Método GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="c383d-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="c383d-110">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="c383d-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c383d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c383d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c383d-112">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c383d-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c383d-113">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="c383d-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c383d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c383d-114">Requirements</span></span>  
 <span data-ttu-id="c383d-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c383d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c383d-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c383d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c383d-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c383d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c383d-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c383d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c383d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c383d-119">See also</span></span>
- [<span data-ttu-id="c383d-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="c383d-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c383d-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c383d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c383d-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="c383d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
