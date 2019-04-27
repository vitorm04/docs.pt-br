---
title: Enumeração CeeSectionAttr
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c317524cefd7ed654e76bdd7051cdcd7653062db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905886"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="e5dad-102">Enumeração CeeSectionAttr</span><span class="sxs-lookup"><span data-stu-id="e5dad-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="e5dad-103">Fornece valores que especificam os atributos de uma seção para uso pela [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e5dad-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5dad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5dad-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="e5dad-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e5dad-105">Members</span></span>  
  
|<span data-ttu-id="e5dad-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e5dad-106">Member</span></span>|<span data-ttu-id="e5dad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5dad-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="e5dad-108">Seção não tem atributos.</span><span class="sxs-lookup"><span data-stu-id="e5dad-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="e5dad-109">Seção contém dados inicializados que podem ser apenas ler, não atualizado.</span><span class="sxs-lookup"><span data-stu-id="e5dad-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="e5dad-110">Seção contém dados inicializados que podem ser lidos ou atualizados.</span><span class="sxs-lookup"><span data-stu-id="e5dad-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="e5dad-111">Seção contém código executável que pode ser lido e executado.</span><span class="sxs-lookup"><span data-stu-id="e5dad-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5dad-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5dad-112">Requirements</span></span>  
 <span data-ttu-id="e5dad-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5dad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5dad-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5dad-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5dad-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e5dad-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5dad-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5dad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dad-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5dad-117">See also</span></span>

- [<span data-ttu-id="e5dad-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e5dad-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
