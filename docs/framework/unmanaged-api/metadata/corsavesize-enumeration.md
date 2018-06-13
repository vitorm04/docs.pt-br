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
ms.openlocfilehash: 66f9f95b0cf19acb677daf7f7401d21cc81864a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447601"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="24b56-102">Enumeração CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="24b56-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="24b56-103">Contém valores que indica o nível de precisão necessária ao consultar o tamanho de um salvamento operação.</span><span class="sxs-lookup"><span data-stu-id="24b56-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b56-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24b56-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="24b56-105">Membros</span><span class="sxs-lookup"><span data-stu-id="24b56-105">Members</span></span>  
  
|<span data-ttu-id="24b56-106">Membro</span><span class="sxs-lookup"><span data-stu-id="24b56-106">Member</span></span>|<span data-ttu-id="24b56-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="24b56-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="24b56-108">Especifica que o valor de retorno deve ser exato.</span><span class="sxs-lookup"><span data-stu-id="24b56-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="24b56-109">Especifica que o valor de retorno deve ser estimado.</span><span class="sxs-lookup"><span data-stu-id="24b56-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="24b56-110">Especifica que tipos descartáveis devem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="24b56-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24b56-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24b56-111">Requirements</span></span>  
 <span data-ttu-id="24b56-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b56-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b56-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="24b56-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="24b56-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="24b56-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24b56-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b56-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b56-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24b56-116">See Also</span></span>  
 [<span data-ttu-id="24b56-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="24b56-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
