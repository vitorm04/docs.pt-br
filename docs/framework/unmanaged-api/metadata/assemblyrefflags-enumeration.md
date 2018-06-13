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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de120516655c1a0578e88ecc2890701ed9fc2f6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443694"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="d8356-102">Enumeração AssemblyRefFlags</span><span class="sxs-lookup"><span data-stu-id="d8356-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="d8356-103">Contém valores que descrevem os recursos de uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="d8356-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8356-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8356-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d8356-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d8356-105">Members</span></span>  
  
|<span data-ttu-id="d8356-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d8356-106">Member</span></span>|<span data-ttu-id="d8356-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8356-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="d8356-108">Especifica que a referência de assembly contém completas, sem hash informações sobre o Editor do assembly.</span><span class="sxs-lookup"><span data-stu-id="d8356-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8356-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8356-109">Requirements</span></span>  
 <span data-ttu-id="d8356-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8356-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8356-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8356-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8356-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8356-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8356-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8356-113">See Also</span></span>  
 [<span data-ttu-id="d8356-114">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="d8356-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="d8356-115">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="d8356-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="d8356-116">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="d8356-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
