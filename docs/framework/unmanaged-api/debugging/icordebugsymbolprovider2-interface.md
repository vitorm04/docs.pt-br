---
title: Interface ICorDebugSymbolProvider2
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db1bba48f4685338f4531e2c11506de338e5c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423215"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="3a048-102">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="3a048-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="3a048-103">Logicamente estende o [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="3a048-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a048-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a048-104">Methods</span></span>  
  
|<span data-ttu-id="3a048-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a048-105">Method</span></span>|<span data-ttu-id="3a048-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a048-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a048-107">Método GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="3a048-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="3a048-108">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="3a048-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="3a048-109">Método GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="3a048-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="3a048-110">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="3a048-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a048-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a048-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a048-112">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3a048-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3a048-113">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="3a048-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a048-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a048-114">Requirements</span></span>  
 <span data-ttu-id="3a048-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a048-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a048-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a048-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a048-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a048-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a048-118">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a048-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a048-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a048-119">See Also</span></span>  
 [<span data-ttu-id="3a048-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="3a048-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="3a048-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3a048-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3a048-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="3a048-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
