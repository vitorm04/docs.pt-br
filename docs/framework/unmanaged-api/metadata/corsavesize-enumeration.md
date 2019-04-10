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
ms.openlocfilehash: bc36468a2016822e884ec3a36a23c75477a00a2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217192"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="728c1-102">Enumeração CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="728c1-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="728c1-103">Contém valores que indicam o nível de precisão necessária ao consultar o tamanho de um salvamento operação.</span><span class="sxs-lookup"><span data-stu-id="728c1-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="728c1-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="728c1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="728c1-105">Members</span></span>  
  
|<span data-ttu-id="728c1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="728c1-106">Member</span></span>|<span data-ttu-id="728c1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="728c1-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="728c1-108">Especifica que o valor de retorno deve ser exato.</span><span class="sxs-lookup"><span data-stu-id="728c1-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="728c1-109">Especifica que o valor de retorno deve ser estimado.</span><span class="sxs-lookup"><span data-stu-id="728c1-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="728c1-110">Especifica que os tipos descartáveis devem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="728c1-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="728c1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="728c1-111">Requirements</span></span>  
 <span data-ttu-id="728c1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="728c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="728c1-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="728c1-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="728c1-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="728c1-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="728c1-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="728c1-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="728c1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="728c1-116">See also</span></span>

- [<span data-ttu-id="728c1-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="728c1-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
