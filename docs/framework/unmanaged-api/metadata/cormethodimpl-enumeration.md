---
title: Enumeração CorMethodImpl
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: a76a7a2d4ad68e367e38e175377aff40ce399346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450199"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="8f8b3-102">Enumeração CorMethodImpl</span><span class="sxs-lookup"><span data-stu-id="8f8b3-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="8f8b3-103">Contém valores que descrevem os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f8b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f8b3-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="8f8b3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8f8b3-105">Members</span></span>  
  
|<span data-ttu-id="8f8b3-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8f8b3-106">Member</span></span>|<span data-ttu-id="8f8b3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f8b3-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="8f8b3-108">Sinalizadores que descrevem o tipo de código.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="8f8b3-109">Especifica que a implementação do método é MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="8f8b3-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="8f8b3-110">Especifica que a implementação do método é nativa.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="8f8b3-111">Especifica que a implementação do método é OPTIl.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="8f8b3-112">Especifica que a implementação do método é fornecida pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="8f8b3-113">Sinalizadores que indicam se o código é gerenciado ou não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="8f8b3-114">Especifica que a implementação do método não é gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="8f8b3-115">Especifica que a implementação do método é gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="8f8b3-116">Especifica que o método está definido.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-116">Specifies that the method is defined.</span></span> <span data-ttu-id="8f8b3-117">Esse sinalizador é usado principalmente em cenários de mesclagem.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="8f8b3-118">Especifica que a assinatura do método não pode ser desconfigurado para uma conversão HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="8f8b3-119">Reservado para uso interno pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="8f8b3-120">Especifica que o método é de thread único por meio de seu corpo.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="8f8b3-121">Especifica que o método não pode estar em linha.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="8f8b3-122">Especifica que o método deve ser embutido, se possível.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="8f8b3-123">Especifica que o método não deve ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="8f8b3-124">O valor máximo válido para um `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="8f8b3-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f8b3-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f8b3-125">Requirements</span></span>  
 <span data-ttu-id="8f8b3-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f8b3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8b3-127">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8f8b3-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8f8b3-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f8b3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8b3-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f8b3-129">See also</span></span>

- [<span data-ttu-id="8f8b3-130">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="8f8b3-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
