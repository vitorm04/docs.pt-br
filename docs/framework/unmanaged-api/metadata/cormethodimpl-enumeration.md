---
title: "Enumeração CorMethodImpl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ee55c0d4ec0d3fb8c18dff570afefeb2eaf25e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="b7b92-102">Enumeração CorMethodImpl</span><span class="sxs-lookup"><span data-stu-id="b7b92-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="b7b92-103">Contém valores que descrevem os recursos de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="b7b92-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7b92-104">Syntax</span></span>  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="b7b92-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b7b92-105">Members</span></span>  
  
|<span data-ttu-id="b7b92-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b7b92-106">Member</span></span>|<span data-ttu-id="b7b92-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7b92-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="b7b92-108">Sinalizadores que descrevem o tipo de código.</span><span class="sxs-lookup"><span data-stu-id="b7b92-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="b7b92-109">Especifica que a implementação do método Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b7b92-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="b7b92-110">Especifica que a implementação do método é nativa.</span><span class="sxs-lookup"><span data-stu-id="b7b92-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="b7b92-111">Especifica que a implementação do método OPTIL.</span><span class="sxs-lookup"><span data-stu-id="b7b92-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="b7b92-112">Especifica que a implementação do método é fornecida pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b7b92-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="b7b92-113">Sinalizadores que indicam se o código é gerenciado ou não.</span><span class="sxs-lookup"><span data-stu-id="b7b92-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="b7b92-114">Especifica que a implementação do método é não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b7b92-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="b7b92-115">Especifica que a implementação do método é gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b7b92-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="b7b92-116">Especifica que o método está definido.</span><span class="sxs-lookup"><span data-stu-id="b7b92-116">Specifies that the method is defined.</span></span> <span data-ttu-id="b7b92-117">Este sinalizador é usado principalmente em cenários de mesclagem.</span><span class="sxs-lookup"><span data-stu-id="b7b92-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="b7b92-118">Especifica que a assinatura do método não pode ser desconfigurada para uma conversão de HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b7b92-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="b7b92-119">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b7b92-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="b7b92-120">Especifica que o método de thread único por meio de seu corpo.</span><span class="sxs-lookup"><span data-stu-id="b7b92-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="b7b92-121">Especifica que o método não pode estar em linha.</span><span class="sxs-lookup"><span data-stu-id="b7b92-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="b7b92-122">Especifica que o método deve ser embutido se possível.</span><span class="sxs-lookup"><span data-stu-id="b7b92-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="b7b92-123">Especifica que o método não deve ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="b7b92-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="b7b92-124">O valor válido máximo para um `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="b7b92-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7b92-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7b92-125">Requirements</span></span>  
 <span data-ttu-id="b7b92-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7b92-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b92-127">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="b7b92-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b7b92-128">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b92-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b92-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7b92-129">See Also</span></span>  
 [<span data-ttu-id="b7b92-130">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="b7b92-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
