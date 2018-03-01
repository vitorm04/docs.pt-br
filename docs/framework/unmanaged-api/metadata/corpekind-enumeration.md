---
title: "Enumeração CorPEKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 612c71db092e7a3474d262c1d601335a5f416791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="8d286-102">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="8d286-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="8d286-103">Contém valores que descrevem um arquivo PE (executável portátil), conforme retornado de uma chamada para [Imetadataimport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d286-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d286-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d286-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="8d286-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8d286-105">Members</span></span>  
  
|<span data-ttu-id="8d286-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8d286-106">Member</span></span>|<span data-ttu-id="8d286-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d286-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="8d286-108">Indica que isso não é um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="8d286-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="8d286-109">Indica que esse arquivo PE contém somente código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d286-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="8d286-110">Indica que esse arquivo PE faz chamadas de Win32.</span><span class="sxs-lookup"><span data-stu-id="8d286-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="8d286-111">Indica que esse arquivo PE é executado em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8d286-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="8d286-112">Indica que esse arquivo PE é o código nativo.</span><span class="sxs-lookup"><span data-stu-id="8d286-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="8d286-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="8d286-113">pe32BitPreferred</span></span>|<span data-ttu-id="8d286-114">Indica que esse arquivo PE é plataforma neutra e prefere ser carregado em um ambiente de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="8d286-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d286-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d286-115">Remarks</span></span>  
 <span data-ttu-id="8d286-116">Esses valores podem ser usados em combinações de bit a bit.</span><span class="sxs-lookup"><span data-stu-id="8d286-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d286-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d286-117">Requirements</span></span>  
 <span data-ttu-id="8d286-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d286-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d286-119">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="8d286-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8d286-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d286-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d286-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d286-121">See Also</span></span>  
 [<span data-ttu-id="8d286-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="8d286-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
