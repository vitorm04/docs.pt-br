---
title: Interface ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180460"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="571ef-102">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="571ef-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="571ef-103">Fornece informações sobre um assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="571ef-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="571ef-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="571ef-104">Methods</span></span>  
  
|<span data-ttu-id="571ef-105">Método</span><span class="sxs-lookup"><span data-stu-id="571ef-105">Method</span></span>|<span data-ttu-id="571ef-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="571ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="571ef-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="571ef-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="571ef-108">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="571ef-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="571ef-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="571ef-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="571ef-110">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="571ef-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="571ef-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="571ef-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="571ef-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="571ef-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="571ef-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="571ef-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="571ef-114">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="571ef-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="571ef-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="571ef-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="571ef-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="571ef-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="571ef-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="571ef-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="571ef-118">Obtém informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="571ef-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="571ef-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="571ef-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="571ef-120">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="571ef-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="571ef-121">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="571ef-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="571ef-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="571ef-122">Requirements</span></span>  
 <span data-ttu-id="571ef-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="571ef-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="571ef-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="571ef-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="571ef-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="571ef-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="571ef-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="571ef-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571ef-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="571ef-127">See also</span></span>

- [<span data-ttu-id="571ef-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="571ef-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="571ef-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="571ef-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
