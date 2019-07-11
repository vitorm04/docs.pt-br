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
ms.openlocfilehash: 05f5d3fbe05ad1e97a1ae61ed0496f314c4ec5cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765962"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="5a1ed-102">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="5a1ed-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="5a1ed-103">Descreve um item a ser adicionado a um despejo personalizado no relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="5a1ed-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a1ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a1ed-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="5a1ed-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5a1ed-105">Members</span></span>  
  
|<span data-ttu-id="5a1ed-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5a1ed-106">Member</span></span>|<span data-ttu-id="5a1ed-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a1ed-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="5a1ed-108">Uma [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) valor que indica o tipo de item a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="5a1ed-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="5a1ed-109">Não usado no momento.</span><span class="sxs-lookup"><span data-stu-id="5a1ed-109">Not currently used.</span></span> <span data-ttu-id="5a1ed-110">Quaisquer itens adicionados à união devem ser maiores do que o tamanho do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5a1ed-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="5a1ed-111">Se um `struct` é obrigatório, você deve alocá-lo separadamente e apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="5a1ed-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a1ed-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a1ed-112">Remarks</span></span>  
 <span data-ttu-id="5a1ed-113">[ICLRErrorReportingManager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) assume um parâmetro do tipo `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="5a1ed-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a1ed-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a1ed-114">Requirements</span></span>  
 <span data-ttu-id="5a1ed-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a1ed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a1ed-116">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="5a1ed-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5a1ed-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5a1ed-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a1ed-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a1ed-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a1ed-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a1ed-119">See also</span></span>

- [<span data-ttu-id="5a1ed-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5a1ed-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
