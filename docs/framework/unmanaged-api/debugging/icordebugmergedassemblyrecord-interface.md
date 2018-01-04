---
title: Interface ICorDebugMergedAssemblyRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6086d1a82b5f086d857ac612a9d454a6ed77ba1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="513c3-102">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="513c3-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="513c3-103">Fornece informações sobre um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="513c3-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="513c3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="513c3-104">Methods</span></span>  
  
|<span data-ttu-id="513c3-105">Método</span><span class="sxs-lookup"><span data-stu-id="513c3-105">Method</span></span>|<span data-ttu-id="513c3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="513c3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="513c3-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="513c3-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="513c3-108">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="513c3-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="513c3-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="513c3-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="513c3-110">Obtém o índice do prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="513c3-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="513c3-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="513c3-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="513c3-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="513c3-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="513c3-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="513c3-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="513c3-114">Obtém a chave pública do assembly token.</span><span class="sxs-lookup"><span data-stu-id="513c3-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="513c3-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="513c3-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="513c3-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="513c3-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="513c3-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="513c3-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="513c3-118">Obtém informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="513c3-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="513c3-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="513c3-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="513c3-120">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="513c3-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="513c3-121">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="513c3-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="513c3-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="513c3-122">Requirements</span></span>  
 <span data-ttu-id="513c3-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="513c3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="513c3-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="513c3-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="513c3-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="513c3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="513c3-126">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="513c3-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513c3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="513c3-127">See Also</span></span>  
 [<span data-ttu-id="513c3-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="513c3-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="513c3-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="513c3-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
