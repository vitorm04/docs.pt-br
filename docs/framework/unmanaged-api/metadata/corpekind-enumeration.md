---
title: Enumeração CorPEKind
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8f830ca7e273b65dc9ec77566a02df6c32cd464
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202385"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="3ffc4-102">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="3ffc4-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="3ffc4-103">Contém valores que descrevem um arquivo executável portátil (PE), conforme retornado de uma chamada para [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="3ffc4-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ffc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ffc4-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3ffc4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3ffc4-105">Members</span></span>  
  
|<span data-ttu-id="3ffc4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3ffc4-106">Member</span></span>|<span data-ttu-id="3ffc4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ffc4-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="3ffc4-108">Indica que não é um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="3ffc4-109">Indica que esse arquivo PE contém somente código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="3ffc4-110">Indica que esse arquivo PE faz chamadas ao Win32.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="3ffc4-111">Indica que esse arquivo PE é executado em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="3ffc4-112">Indica que esse arquivo PE é código nativo.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="3ffc4-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="3ffc4-113">pe32BitPreferred</span></span>|<span data-ttu-id="3ffc4-114">Indica que esse arquivo PE é neutro de plataforma e prefere a ser carregado em um ambiente de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ffc4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ffc4-115">Remarks</span></span>  
 <span data-ttu-id="3ffc4-116">Esses valores podem ser usados em combinações de bit a bit.</span><span class="sxs-lookup"><span data-stu-id="3ffc4-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ffc4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ffc4-117">Requirements</span></span>  
 <span data-ttu-id="3ffc4-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ffc4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ffc4-119">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3ffc4-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3ffc4-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ffc4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ffc4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ffc4-121">See also</span></span>

- [<span data-ttu-id="3ffc4-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3ffc4-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
