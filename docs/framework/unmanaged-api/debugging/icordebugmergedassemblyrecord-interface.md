---
title: ICorDebugMergedAssemblyRecord Interface
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f42b8d6eb1a35052b25fda6e7cc9c7d00836df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559353"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="344cd-102">ICorDebugMergedAssemblyRecord Interface</span><span class="sxs-lookup"><span data-stu-id="344cd-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="344cd-103">Fornece informações sobre um assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="344cd-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="344cd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="344cd-104">Methods</span></span>  
  
|<span data-ttu-id="344cd-105">Método</span><span class="sxs-lookup"><span data-stu-id="344cd-105">Method</span></span>|<span data-ttu-id="344cd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="344cd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="344cd-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="344cd-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="344cd-108">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="344cd-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="344cd-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="344cd-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="344cd-110">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="344cd-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="344cd-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="344cd-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="344cd-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="344cd-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="344cd-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="344cd-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="344cd-114">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="344cd-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="344cd-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="344cd-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="344cd-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="344cd-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="344cd-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="344cd-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="344cd-118">Obtém informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="344cd-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="344cd-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="344cd-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="344cd-120">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="344cd-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="344cd-121">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="344cd-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="344cd-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="344cd-122">Requirements</span></span>  
 <span data-ttu-id="344cd-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="344cd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="344cd-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="344cd-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="344cd-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="344cd-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="344cd-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="344cd-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344cd-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="344cd-127">See also</span></span>
- [<span data-ttu-id="344cd-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="344cd-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="344cd-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="344cd-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
