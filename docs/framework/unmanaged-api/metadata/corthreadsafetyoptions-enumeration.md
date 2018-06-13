---
title: Enumeração CorThreadSafetyOptions
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3407fcac420b8129dd39eabf84aec84b58651944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442821"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="f5c1b-102">Enumeração CorThreadSafetyOptions</span><span class="sxs-lookup"><span data-stu-id="f5c1b-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="f5c1b-103">Especifica os sinalizadores para selecionar opções para acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="f5c1b-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c1b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5c1b-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="f5c1b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f5c1b-105">Members</span></span>  
  
|<span data-ttu-id="f5c1b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f5c1b-106">Member</span></span>|<span data-ttu-id="f5c1b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5c1b-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="f5c1b-108">Valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f5c1b-108">Default value.</span></span> <span data-ttu-id="f5c1b-109">Mesmo que `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="f5c1b-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="f5c1b-110">Indica que um bloqueio de leitor/gravador não pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="f5c1b-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="f5c1b-111">Indica que um bloqueio de leitor/gravador pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="f5c1b-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5c1b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5c1b-112">Requirements</span></span>  
 <span data-ttu-id="f5c1b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c1b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c1b-114">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="f5c1b-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f5c1b-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c1b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c1b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5c1b-116">See Also</span></span>  
 [<span data-ttu-id="f5c1b-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f5c1b-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
