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
ms.openlocfilehash: ce6f5993b9c1aeb63e121b3567ee468cea1c9318
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007514"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="73fe5-102">Enumeração CorRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="73fe5-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="73fe5-103">Especifica sinalizadores para controlar quais itens referenciados são convertidos em suas definições a fim de otimizar o código.</span><span class="sxs-lookup"><span data-stu-id="73fe5-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fe5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73fe5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="73fe5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="73fe5-105">Members</span></span>  
  
|<span data-ttu-id="73fe5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="73fe5-106">Member</span></span>|<span data-ttu-id="73fe5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="73fe5-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="73fe5-108">Especifica que referências de tipo e referências de membro devem ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="73fe5-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="73fe5-109">Esse é o valor padrão ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).</span><span class="sxs-lookup"><span data-stu-id="73fe5-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="73fe5-110">Especifica que todos os itens referenciados devem ser convertidos em definições.</span><span class="sxs-lookup"><span data-stu-id="73fe5-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="73fe5-111">Especifica que nenhum item referenciado deve ser convertido em definições.</span><span class="sxs-lookup"><span data-stu-id="73fe5-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="73fe5-112">Especifica que apenas referências de tipo devem ser convertidas em definições de tipo.</span><span class="sxs-lookup"><span data-stu-id="73fe5-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="73fe5-113">Especifica que somente referências de membro devem ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="73fe5-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="73fe5-114">Ou seja, as referências de membro devem ser convertidas em definições de método ou definições de campo.</span><span class="sxs-lookup"><span data-stu-id="73fe5-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73fe5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73fe5-115">Requirements</span></span>  
 <span data-ttu-id="73fe5-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73fe5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73fe5-117">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="73fe5-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="73fe5-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73fe5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fe5-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="73fe5-119">See also</span></span>

- [<span data-ttu-id="73fe5-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="73fe5-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
