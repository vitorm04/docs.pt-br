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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045377"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="0334f-102">Enumeração CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="0334f-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="0334f-103">Contém valores que indicam o nível de precisão necessária ao consultar o tamanho de um salvamento operação.</span><span class="sxs-lookup"><span data-stu-id="0334f-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0334f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0334f-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="0334f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0334f-105">Members</span></span>  
  
|<span data-ttu-id="0334f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0334f-106">Member</span></span>|<span data-ttu-id="0334f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0334f-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="0334f-108">Especifica que o valor de retorno deve ser exato.</span><span class="sxs-lookup"><span data-stu-id="0334f-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="0334f-109">Especifica que o valor de retorno deve ser estimado.</span><span class="sxs-lookup"><span data-stu-id="0334f-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="0334f-110">Especifica que os tipos descartáveis devem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="0334f-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0334f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0334f-111">Requirements</span></span>  
 <span data-ttu-id="0334f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0334f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0334f-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0334f-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0334f-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0334f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0334f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0334f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0334f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0334f-116">See also</span></span>

- [<span data-ttu-id="0334f-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="0334f-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
