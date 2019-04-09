---
title: Interface ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180460"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="29108-102">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="29108-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="29108-103">Fornece informações sobre um assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="29108-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29108-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="29108-104">Methods</span></span>  
  
|<span data-ttu-id="29108-105">Método</span><span class="sxs-lookup"><span data-stu-id="29108-105">Method</span></span>|<span data-ttu-id="29108-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="29108-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29108-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="29108-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="29108-108">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="29108-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="29108-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="29108-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="29108-110">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="29108-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="29108-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="29108-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="29108-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="29108-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="29108-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="29108-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="29108-114">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="29108-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="29108-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="29108-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="29108-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="29108-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="29108-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="29108-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="29108-118">Obtém informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="29108-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29108-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="29108-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29108-120">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="29108-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="29108-121">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="29108-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29108-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29108-122">Requirements</span></span>  
 <span data-ttu-id="29108-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29108-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29108-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29108-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29108-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29108-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="29108-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="29108-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29108-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29108-127">See also</span></span>

- [<span data-ttu-id="29108-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="29108-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="29108-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="29108-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
