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
ms.openlocfilehash: c8118de9f4fc6a4f2820b88685b9b87c498328b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="13022-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="13022-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="13022-103">Fornece valores de sinalizador usados para registro ao instalar um módulo ou imagem composta.</span><span class="sxs-lookup"><span data-stu-id="13022-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13022-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13022-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="13022-105">Membros</span><span class="sxs-lookup"><span data-stu-id="13022-105">Members</span></span>  
  
|<span data-ttu-id="13022-106">Membro</span><span class="sxs-lookup"><span data-stu-id="13022-106">Member</span></span>|<span data-ttu-id="13022-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="13022-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="13022-108">Especifica que os arquivos não devem ser copiados no destino.</span><span class="sxs-lookup"><span data-stu-id="13022-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="13022-109">Especifica que o módulo ou composição é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="13022-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="13022-110">Especifica que o módulo ou composição tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="13022-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13022-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13022-111">Requirements</span></span>  
 <span data-ttu-id="13022-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13022-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13022-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13022-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13022-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="13022-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13022-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13022-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13022-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13022-116">See Also</span></span>  
 [<span data-ttu-id="13022-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="13022-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
