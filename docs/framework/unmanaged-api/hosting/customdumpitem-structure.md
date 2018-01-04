---
title: Estrutura CustomDumpItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CustomDumpItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CustomDumpItem
helpviewer_keywords: CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47fd4e1dd3889cc7eeaa37457b47d9b2fd6dd8b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="77dd9-102">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="77dd9-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="77dd9-103">Descreve um item a ser adicionado a um despejo personalizado nos relatórios de erros.</span><span class="sxs-lookup"><span data-stu-id="77dd9-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77dd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77dd9-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="77dd9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="77dd9-105">Members</span></span>  
  
|<span data-ttu-id="77dd9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="77dd9-106">Member</span></span>|<span data-ttu-id="77dd9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="77dd9-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="77dd9-108">Um [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) valor que indica o tipo de item a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="77dd9-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="77dd9-109">Não usado no momento.</span><span class="sxs-lookup"><span data-stu-id="77dd9-109">Not currently used.</span></span> <span data-ttu-id="77dd9-110">Quaisquer itens adicionados à união devem ser maiores do que o tamanho do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="77dd9-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="77dd9-111">Se um `struct` é necessária, você deve alocá-lo separadamente e aponte para ela.</span><span class="sxs-lookup"><span data-stu-id="77dd9-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77dd9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="77dd9-112">Remarks</span></span>  
 <span data-ttu-id="77dd9-113">[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) usa um parâmetro do tipo `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="77dd9-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77dd9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77dd9-114">Requirements</span></span>  
 <span data-ttu-id="77dd9-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77dd9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77dd9-116">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="77dd9-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="77dd9-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77dd9-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77dd9-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77dd9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77dd9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77dd9-119">See Also</span></span>  
 [<span data-ttu-id="77dd9-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="77dd9-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
