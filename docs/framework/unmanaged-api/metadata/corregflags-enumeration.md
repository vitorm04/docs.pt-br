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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104956"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="c3cf7-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="c3cf7-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="c3cf7-103">Fornece valores de sinalizador usados para registro ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3cf7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3cf7-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c3cf7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c3cf7-105">Members</span></span>  
  
|<span data-ttu-id="c3cf7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c3cf7-106">Member</span></span>|<span data-ttu-id="c3cf7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3cf7-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="c3cf7-108">Especifica que os arquivos não devem ser copiados no destino.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="c3cf7-109">Especifica que o módulo ou composto é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="c3cf7-110">Especifica que o módulo ou composição tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3cf7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3cf7-111">Requirements</span></span>  
 <span data-ttu-id="c3cf7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3cf7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3cf7-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3cf7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3cf7-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c3cf7-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c3cf7-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c3cf7-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3cf7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3cf7-116">See also</span></span>

- [<span data-ttu-id="c3cf7-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c3cf7-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
