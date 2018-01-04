---
title: "Enumeração CorRegFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRegFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRegFlags
helpviewer_keywords: CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f2dcc60d41369250409cccf5b340e98f0cb4ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="f6441-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="f6441-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="f6441-103">Fornece valores de sinalizador usados para registro ao instalar um módulo ou imagem composta.</span><span class="sxs-lookup"><span data-stu-id="f6441-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6441-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6441-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f6441-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f6441-105">Members</span></span>  
  
|<span data-ttu-id="f6441-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f6441-106">Member</span></span>|<span data-ttu-id="f6441-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6441-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="f6441-108">Especifica que os arquivos não devem ser copiados no destino.</span><span class="sxs-lookup"><span data-stu-id="f6441-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="f6441-109">Especifica que o módulo ou composição é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="f6441-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="f6441-110">Especifica que o módulo ou composição tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="f6441-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6441-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6441-111">Requirements</span></span>  
 <span data-ttu-id="f6441-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6441-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6441-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6441-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6441-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f6441-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6441-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6441-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6441-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6441-116">See Also</span></span>  
 [<span data-ttu-id="f6441-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f6441-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
