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
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138279"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="30202-102">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="30202-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="30202-103">Descreve um item a ser adicionado a um despejo personalizado no relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="30202-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30202-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30202-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="30202-105">Membros</span><span class="sxs-lookup"><span data-stu-id="30202-105">Members</span></span>  
  
|<span data-ttu-id="30202-106">Membro</span><span class="sxs-lookup"><span data-stu-id="30202-106">Member</span></span>|<span data-ttu-id="30202-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="30202-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="30202-108">Um valor [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) que indica o tipo de item a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="30202-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="30202-109">Não usado no momento.</span><span class="sxs-lookup"><span data-stu-id="30202-109">Not currently used.</span></span> <span data-ttu-id="30202-110">Os itens adicionados à União não devem ser maiores do que o tamanho do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="30202-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="30202-111">Se um `struct` for necessário, você deverá alocá-lo separadamente e apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="30202-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30202-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="30202-112">Remarks</span></span>  
 <span data-ttu-id="30202-113">[ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) usa um parâmetro do tipo `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="30202-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30202-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30202-114">Requirements</span></span>  
 <span data-ttu-id="30202-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30202-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30202-116">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="30202-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="30202-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="30202-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30202-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30202-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30202-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30202-119">See also</span></span>

- [<span data-ttu-id="30202-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="30202-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
