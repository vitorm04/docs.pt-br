---
title: "Enumeração CeeSectionAttr"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionAttr
helpviewer_keywords: CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f0c87c0e5703f13cf843ca5a4213440af71bd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="6715d-102">Enumeração CeeSectionAttr</span><span class="sxs-lookup"><span data-stu-id="6715d-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="6715d-103">Fornece valores que especificam os atributos de uma seção para uso pelo [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6715d-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6715d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6715d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6715d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6715d-105">Members</span></span>  
  
|<span data-ttu-id="6715d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6715d-106">Member</span></span>|<span data-ttu-id="6715d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6715d-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="6715d-108">Seção não tem atributos.</span><span class="sxs-lookup"><span data-stu-id="6715d-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="6715d-109">Seção contém dados inicializados que podem ser somente leitura, não atualizado.</span><span class="sxs-lookup"><span data-stu-id="6715d-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="6715d-110">Seção contém dados inicializados que podem ser lidos ou atualizados.</span><span class="sxs-lookup"><span data-stu-id="6715d-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="6715d-111">Seção contém o código executável que pode ser lido e executado.</span><span class="sxs-lookup"><span data-stu-id="6715d-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6715d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6715d-112">Requirements</span></span>  
 <span data-ttu-id="6715d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6715d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6715d-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6715d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6715d-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6715d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6715d-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6715d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6715d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6715d-117">See Also</span></span>  
 [<span data-ttu-id="6715d-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="6715d-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
