---
title: Enumeração CorSaveSize
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f756e8688299fbe9d53822851be83703f4aa6348
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550624"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="c0cc6-102">Enumeração CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="c0cc6-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="c0cc6-103">Contém valores que indicam o nível de precisão necessária ao consultar o tamanho de um salvamento operação.</span><span class="sxs-lookup"><span data-stu-id="c0cc6-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0cc6-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="c0cc6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c0cc6-105">Members</span></span>  
  
|<span data-ttu-id="c0cc6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c0cc6-106">Member</span></span>|<span data-ttu-id="c0cc6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0cc6-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="c0cc6-108">Especifica que o valor de retorno deve ser exato.</span><span class="sxs-lookup"><span data-stu-id="c0cc6-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="c0cc6-109">Especifica que o valor de retorno deve ser estimado.</span><span class="sxs-lookup"><span data-stu-id="c0cc6-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="c0cc6-110">Especifica que os tipos descartáveis devem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="c0cc6-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0cc6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0cc6-111">Requirements</span></span>  
 <span data-ttu-id="c0cc6-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0cc6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0cc6-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c0cc6-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c0cc6-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c0cc6-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0cc6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0cc6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0cc6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0cc6-116">See also</span></span>
- [<span data-ttu-id="c0cc6-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c0cc6-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
