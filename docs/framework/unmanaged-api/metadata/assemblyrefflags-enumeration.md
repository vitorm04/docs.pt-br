---
title: Enumeração AssemblyRefFlags
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 23d293a87112c62cb2127b435faeca258a7de226
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444230"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="62fae-102">Enumeração AssemblyRefFlags</span><span class="sxs-lookup"><span data-stu-id="62fae-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="62fae-103">Contém valores que descrevem os recursos de uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="62fae-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62fae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62fae-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="62fae-105">Membros</span><span class="sxs-lookup"><span data-stu-id="62fae-105">Members</span></span>  
  
|<span data-ttu-id="62fae-106">Membro</span><span class="sxs-lookup"><span data-stu-id="62fae-106">Member</span></span>|<span data-ttu-id="62fae-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="62fae-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="62fae-108">Especifica que a referência de assembly contém informações completas e sem hash sobre o Publicador do assembly.</span><span class="sxs-lookup"><span data-stu-id="62fae-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62fae-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="62fae-109">Requirements</span></span>  
 <span data-ttu-id="62fae-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62fae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62fae-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="62fae-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62fae-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62fae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62fae-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62fae-113">See also</span></span>

- [<span data-ttu-id="62fae-114">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="62fae-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="62fae-115">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="62fae-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="62fae-116">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="62fae-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
