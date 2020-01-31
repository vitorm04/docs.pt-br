---
title: Interface ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793064"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="66638-102">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="66638-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="66638-103">Fornece informações sobre um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="66638-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66638-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="66638-104">Methods</span></span>  
  
|<span data-ttu-id="66638-105">Método</span><span class="sxs-lookup"><span data-stu-id="66638-105">Method</span></span>|<span data-ttu-id="66638-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="66638-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66638-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="66638-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="66638-108">Obtém a cadeia de caracteres do nome da cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="66638-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="66638-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="66638-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="66638-110">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="66638-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="66638-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="66638-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="66638-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="66638-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="66638-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="66638-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="66638-114">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="66638-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="66638-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="66638-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="66638-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="66638-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="66638-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="66638-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="66638-118">Obtém as informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="66638-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66638-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="66638-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66638-120">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="66638-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="66638-121">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="66638-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66638-122">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="66638-122">Requirements</span></span>  
 <span data-ttu-id="66638-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66638-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66638-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66638-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66638-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66638-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66638-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66638-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66638-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="66638-127">See also</span></span>

- [<span data-ttu-id="66638-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="66638-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="66638-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="66638-129">Debugging</span></span>](index.md)
