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
ms.openlocfilehash: 8fe6216e11a64ea182d796247d888b862b1e8377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177934"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="8833d-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="8833d-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="8833d-103">Fornece valores de bandeira usados para registro ao instalar um módulo ou imagem composta.</span><span class="sxs-lookup"><span data-stu-id="8833d-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8833d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8833d-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8833d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8833d-105">Members</span></span>  
  
|<span data-ttu-id="8833d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8833d-106">Member</span></span>|<span data-ttu-id="8833d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8833d-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="8833d-108">Especifica que os arquivos não devem ser copiados para o destino.</span><span class="sxs-lookup"><span data-stu-id="8833d-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="8833d-109">Especifica que o módulo ou composto é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="8833d-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="8833d-110">Especifica que o módulo ou composto tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="8833d-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8833d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8833d-111">Requirements</span></span>  
 <span data-ttu-id="8833d-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8833d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8833d-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8833d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8833d-114">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8833d-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8833d-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8833d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8833d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="8833d-116">See also</span></span>

- [<span data-ttu-id="8833d-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="8833d-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
