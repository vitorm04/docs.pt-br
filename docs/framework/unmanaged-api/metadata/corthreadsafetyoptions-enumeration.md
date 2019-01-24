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
ms.openlocfilehash: b460c2c4b0d38ec46ee9d7341de9b320a2ecaa7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594636"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="2edd6-102">Enumeração CorThreadSafetyOptions</span><span class="sxs-lookup"><span data-stu-id="2edd6-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="2edd6-103">Especifica os sinalizadores para selecionar opções para acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="2edd6-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2edd6-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="2edd6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2edd6-105">Members</span></span>  
  
|<span data-ttu-id="2edd6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2edd6-106">Member</span></span>|<span data-ttu-id="2edd6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2edd6-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="2edd6-108">Valor padrão.</span><span class="sxs-lookup"><span data-stu-id="2edd6-108">Default value.</span></span> <span data-ttu-id="2edd6-109">Mesmo que `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="2edd6-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="2edd6-110">Indica que um bloqueio de leitor/gravador não pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="2edd6-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="2edd6-111">Indica que um bloqueio de leitor/gravador pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="2edd6-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2edd6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2edd6-112">Requirements</span></span>  
 <span data-ttu-id="2edd6-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2edd6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2edd6-114">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2edd6-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2edd6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2edd6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edd6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2edd6-116">See also</span></span>
- [<span data-ttu-id="2edd6-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2edd6-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
