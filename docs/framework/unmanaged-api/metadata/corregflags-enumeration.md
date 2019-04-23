---
title: Enumeração CorRegFlags
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6b303fa7569712c854e8dc4e7513d8608e2519
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104956"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="a5134-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="a5134-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="a5134-103">Fornece valores de sinalizador usados para registro ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="a5134-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5134-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5134-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a5134-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a5134-105">Members</span></span>  
  
|<span data-ttu-id="a5134-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a5134-106">Member</span></span>|<span data-ttu-id="a5134-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5134-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="a5134-108">Especifica que os arquivos não devem ser copiados no destino.</span><span class="sxs-lookup"><span data-stu-id="a5134-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="a5134-109">Especifica que o módulo ou composto é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="a5134-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="a5134-110">Especifica que o módulo ou composição tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="a5134-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5134-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5134-111">Requirements</span></span>  
 <span data-ttu-id="a5134-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5134-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5134-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a5134-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5134-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a5134-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5134-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5134-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5134-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5134-116">See also</span></span>

- [<span data-ttu-id="a5134-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="a5134-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
