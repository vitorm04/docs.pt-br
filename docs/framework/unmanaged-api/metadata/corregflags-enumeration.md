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
ms.openlocfilehash: 52b59a4e52d3e0cda7353ec1b39c5307bd7b218e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532260"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="cadd4-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="cadd4-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="cadd4-103">Fornece valores de sinalizador usados para registro ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="cadd4-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cadd4-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cadd4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cadd4-105">Members</span></span>  
  
|<span data-ttu-id="cadd4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cadd4-106">Member</span></span>|<span data-ttu-id="cadd4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cadd4-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="cadd4-108">Especifica que os arquivos não devem ser copiados no destino.</span><span class="sxs-lookup"><span data-stu-id="cadd4-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="cadd4-109">Especifica que o módulo ou composto é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="cadd4-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="cadd4-110">Especifica que o módulo ou composição tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="cadd4-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cadd4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cadd4-111">Requirements</span></span>  
 <span data-ttu-id="cadd4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cadd4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadd4-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cadd4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cadd4-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cadd4-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cadd4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadd4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadd4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cadd4-116">See also</span></span>
- [<span data-ttu-id="cadd4-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="cadd4-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
