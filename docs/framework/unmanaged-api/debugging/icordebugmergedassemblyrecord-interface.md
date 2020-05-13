---
title: Interface ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 721f6c1cf468b3b518d2ea213588ae2410249690
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208714"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="c4230-102">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="c4230-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="c4230-103">Fornece informações sobre um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="c4230-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4230-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c4230-104">Methods</span></span>  
  
|<span data-ttu-id="c4230-105">Método</span><span class="sxs-lookup"><span data-stu-id="c4230-105">Method</span></span>|<span data-ttu-id="c4230-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4230-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4230-107">Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="c4230-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="c4230-108">Obtém a cadeia de caracteres do nome da cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4230-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="c4230-109">Método GetIndex</span><span class="sxs-lookup"><span data-stu-id="c4230-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="c4230-110">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4230-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="c4230-111">Método GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="c4230-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="c4230-112">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4230-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="c4230-113">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="c4230-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="c4230-114">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4230-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="c4230-115">Método GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="c4230-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="c4230-116">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4230-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="c4230-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="c4230-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="c4230-118">Obtém as informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4230-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4230-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4230-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4230-120">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c4230-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c4230-121">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="c4230-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4230-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4230-122">Requirements</span></span>  
 <span data-ttu-id="c4230-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4230-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4230-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4230-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4230-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4230-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4230-126">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4230-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4230-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4230-127">See also</span></span>

- [<span data-ttu-id="c4230-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c4230-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c4230-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="c4230-129">Debugging</span></span>](index.md)
