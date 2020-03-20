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
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176468"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="7ba05-102">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="7ba05-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="7ba05-103">Descreve um item a ser adicionado a um dump personalizado no relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="7ba05-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ba05-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="7ba05-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7ba05-105">Members</span></span>  
  
|<span data-ttu-id="7ba05-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7ba05-106">Member</span></span>|<span data-ttu-id="7ba05-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba05-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="7ba05-108">Um [valor ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) que indica o tipo de item a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="7ba05-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="7ba05-109">Não usado no momento.</span><span class="sxs-lookup"><span data-stu-id="7ba05-109">Not currently used.</span></span> <span data-ttu-id="7ba05-110">Todos os itens adicionados à união não devem ser maiores do que o tamanho do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="7ba05-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="7ba05-111">Se `struct` for necessário, você deve alocá-lo separadamente e apontá-lo.</span><span class="sxs-lookup"><span data-stu-id="7ba05-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ba05-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ba05-112">Remarks</span></span>  
 <span data-ttu-id="7ba05-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) leva um parâmetro `CustomDumpItem`do tipo .</span><span class="sxs-lookup"><span data-stu-id="7ba05-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ba05-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ba05-114">Requirements</span></span>  
 <span data-ttu-id="7ba05-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ba05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ba05-116">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7ba05-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7ba05-117">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ba05-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ba05-118">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ba05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba05-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7ba05-119">See also</span></span>

- [<span data-ttu-id="7ba05-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7ba05-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
