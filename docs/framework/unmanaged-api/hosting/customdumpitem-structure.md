---
title: Estrutura CustomDumpItem
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9000f35e9a8f7ecc6c40cf0ef9c220fc9f4f9c10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185920"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="1bf5b-102">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="1bf5b-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="1bf5b-103">Descreve um item a ser adicionado a um despejo personalizado no relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bf5b-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="1bf5b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1bf5b-105">Members</span></span>  
  
|<span data-ttu-id="1bf5b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1bf5b-106">Member</span></span>|<span data-ttu-id="1bf5b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bf5b-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="1bf5b-108">Uma [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) valor que indica o tipo de item a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="1bf5b-109">Não usado no momento.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-109">Not currently used.</span></span> <span data-ttu-id="1bf5b-110">Quaisquer itens adicionados à união devem ser maiores do que o tamanho do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="1bf5b-111">Se um `struct` é obrigatório, você deve alocá-lo separadamente e apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bf5b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bf5b-112">Remarks</span></span>  
 <span data-ttu-id="1bf5b-113">[ICLRErrorReportingManager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) assume um parâmetro do tipo `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bf5b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1bf5b-114">Requirements</span></span>  
 <span data-ttu-id="1bf5b-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bf5b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bf5b-116">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="1bf5b-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1bf5b-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1bf5b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1bf5b-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1bf5b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf5b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bf5b-119">See also</span></span>

- [<span data-ttu-id="1bf5b-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="1bf5b-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
