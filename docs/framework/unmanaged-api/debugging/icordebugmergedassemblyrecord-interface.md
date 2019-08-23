---
title: Interface ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd7a5f630bcf97277a4f98f2408ecaf04883fa3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916983"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="019ab-102">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="019ab-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="019ab-103">Fornece informações sobre um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="019ab-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="019ab-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="019ab-104">Methods</span></span>  
  
|<span data-ttu-id="019ab-105">Método</span><span class="sxs-lookup"><span data-stu-id="019ab-105">Method</span></span>|<span data-ttu-id="019ab-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="019ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="019ab-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="019ab-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="019ab-108">Obtém a cadeia de caracteres do nome da cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="019ab-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="019ab-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="019ab-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="019ab-110">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="019ab-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="019ab-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="019ab-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="019ab-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="019ab-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="019ab-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="019ab-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="019ab-114">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="019ab-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="019ab-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="019ab-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="019ab-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="019ab-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="019ab-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="019ab-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="019ab-118">Obtém as informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="019ab-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="019ab-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="019ab-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="019ab-120">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="019ab-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="019ab-121">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="019ab-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="019ab-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="019ab-122">Requirements</span></span>  
 <span data-ttu-id="019ab-123">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="019ab-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="019ab-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="019ab-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="019ab-125">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="019ab-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="019ab-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="019ab-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019ab-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="019ab-127">See also</span></span>

- [<span data-ttu-id="019ab-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="019ab-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="019ab-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="019ab-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
