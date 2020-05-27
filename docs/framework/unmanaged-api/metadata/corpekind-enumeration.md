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
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007553"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="80de8-102">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="80de8-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="80de8-103">Contém valores que descrevem um arquivo executável portátil (PE), como retornado de uma chamada para [IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="80de8-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80de8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80de8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="80de8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="80de8-105">Members</span></span>  
  
|<span data-ttu-id="80de8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="80de8-106">Member</span></span>|<span data-ttu-id="80de8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="80de8-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="80de8-108">Indica que este não é um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="80de8-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="80de8-109">Indica que este arquivo PE contém apenas código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80de8-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="80de8-110">Indica que esse arquivo PE faz chamadas Win32.</span><span class="sxs-lookup"><span data-stu-id="80de8-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="80de8-111">Indica que este arquivo PE é executado em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="80de8-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="80de8-112">Indica que este arquivo PE é um código nativo.</span><span class="sxs-lookup"><span data-stu-id="80de8-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="80de8-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="80de8-113">pe32BitPreferred</span></span>|<span data-ttu-id="80de8-114">Indica que este arquivo PE é de plataforma neutra e prefere ser carregado em um ambiente de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="80de8-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80de8-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="80de8-115">Remarks</span></span>  
 <span data-ttu-id="80de8-116">Esses valores podem ser usados em combinações de bits.</span><span class="sxs-lookup"><span data-stu-id="80de8-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80de8-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80de8-117">Requirements</span></span>  
 <span data-ttu-id="80de8-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80de8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80de8-119">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="80de8-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="80de8-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80de8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80de8-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="80de8-121">See also</span></span>

- [<span data-ttu-id="80de8-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="80de8-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
