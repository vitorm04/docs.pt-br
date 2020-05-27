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
ms.openlocfilehash: 1307f555c9d8b6d28febcf25db89ae856c143d71
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009399"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="2d3e9-102">Enumeração AssemblyRefFlags</span><span class="sxs-lookup"><span data-stu-id="2d3e9-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="2d3e9-103">Contém valores que descrevem os recursos de uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="2d3e9-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d3e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d3e9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2d3e9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2d3e9-105">Members</span></span>  
  
|<span data-ttu-id="2d3e9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2d3e9-106">Member</span></span>|<span data-ttu-id="2d3e9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d3e9-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="2d3e9-108">Especifica que a referência de assembly contém informações completas e sem hash sobre o Publicador do assembly.</span><span class="sxs-lookup"><span data-stu-id="2d3e9-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d3e9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d3e9-109">Requirements</span></span>  
 <span data-ttu-id="2d3e9-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d3e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d3e9-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d3e9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d3e9-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d3e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3e9-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2d3e9-113">See also</span></span>

- [<span data-ttu-id="2d3e9-114">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2d3e9-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="2d3e9-115">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="2d3e9-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2d3e9-116">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="2d3e9-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
