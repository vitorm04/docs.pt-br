---
title: Enumeração CorRefToDefCheck
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82abeb0ce3db075d794787bb1fcd5bc18321bef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093885"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="5b1e2-102">Enumeração CorRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="5b1e2-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="5b1e2-103">Especifica sinalizadores para controlar quais itens referenciados são convertidos em suas definições para otimizar o código.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b1e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b1e2-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="5b1e2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5b1e2-105">Members</span></span>  
  
|<span data-ttu-id="5b1e2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5b1e2-106">Member</span></span>|<span data-ttu-id="5b1e2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b1e2-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="5b1e2-108">Especifica que as referências de tipo e membro devem ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="5b1e2-109">Esse é o valor padrão (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="5b1e2-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="5b1e2-110">Especifica que todos os itens referenciados devem ser convertidos em definições.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="5b1e2-111">Especifica que nenhum item referenciado deve ser convertido para definições.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="5b1e2-112">Especifica que somente as referências de tipo devem ser convertidas para definições de tipo.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="5b1e2-113">Especifica que somente as referências de membro devem ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="5b1e2-114">Ou seja, as referências de membro devem ser convertidas em definições de método ou definições de campo.</span><span class="sxs-lookup"><span data-stu-id="5b1e2-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b1e2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b1e2-115">Requirements</span></span>  
 <span data-ttu-id="5b1e2-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b1e2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b1e2-117">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5b1e2-117">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="5b1e2-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5b1e2-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b1e2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b1e2-119">See also</span></span>

- [<span data-ttu-id="5b1e2-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="5b1e2-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
