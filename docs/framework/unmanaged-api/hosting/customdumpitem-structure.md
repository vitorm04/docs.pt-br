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
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616431"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="57f45-102">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="57f45-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="57f45-103">Descreve um item a ser adicionado a um despejo personalizado no relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="57f45-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f45-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57f45-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="57f45-105">Membros</span><span class="sxs-lookup"><span data-stu-id="57f45-105">Members</span></span>  
  
|<span data-ttu-id="57f45-106">Membro</span><span class="sxs-lookup"><span data-stu-id="57f45-106">Member</span></span>|<span data-ttu-id="57f45-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="57f45-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="57f45-108">Um valor [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) que indica o tipo de item a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="57f45-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="57f45-109">Não usado no momento.</span><span class="sxs-lookup"><span data-stu-id="57f45-109">Not currently used.</span></span> <span data-ttu-id="57f45-110">Os itens adicionados à União não devem ser maiores do que o tamanho do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="57f45-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="57f45-111">Se `struct` for necessário, você deverá alocá-lo separadamente e apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="57f45-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57f45-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="57f45-112">Remarks</span></span>  
 <span data-ttu-id="57f45-113">[ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) usa um parâmetro do tipo `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="57f45-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57f45-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57f45-114">Requirements</span></span>  
 <span data-ttu-id="57f45-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57f45-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f45-116">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="57f45-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="57f45-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="57f45-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57f45-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57f45-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f45-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="57f45-119">See also</span></span>

- [<span data-ttu-id="57f45-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="57f45-120">Hosting Structures</span></span>](hosting-structures.md)
