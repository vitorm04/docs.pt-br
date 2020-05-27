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
ms.openlocfilehash: d8d7a43848929e49a8cb48fb957f37213ac78f2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007345"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="122ac-102">Enumeração CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="122ac-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="122ac-103">Fornece valores de sinalizador usados para registro ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="122ac-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="122ac-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="122ac-105">Membros</span><span class="sxs-lookup"><span data-stu-id="122ac-105">Members</span></span>  
  
|<span data-ttu-id="122ac-106">Membro</span><span class="sxs-lookup"><span data-stu-id="122ac-106">Member</span></span>|<span data-ttu-id="122ac-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="122ac-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="122ac-108">Especifica que os arquivos não devem ser copiados para o destino.</span><span class="sxs-lookup"><span data-stu-id="122ac-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="122ac-109">Especifica que o módulo ou composto é uma configuração.</span><span class="sxs-lookup"><span data-stu-id="122ac-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="122ac-110">Especifica que o módulo ou composto tem referências de classe.</span><span class="sxs-lookup"><span data-stu-id="122ac-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="122ac-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="122ac-111">Requirements</span></span>  
 <span data-ttu-id="122ac-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122ac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122ac-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="122ac-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="122ac-114">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="122ac-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="122ac-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122ac-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="122ac-116">See also</span></span>

- [<span data-ttu-id="122ac-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="122ac-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
