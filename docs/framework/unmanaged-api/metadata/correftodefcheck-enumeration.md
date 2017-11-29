---
title: "Enumeração CorRefToDefCheck"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5144cd3ac261647c04ec7e3e27e28618c94fb439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="cf60e-102">Enumeração CorRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="cf60e-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="cf60e-103">Especifica os sinalizadores para controlar quais itens referenciados são convertidos para suas definições para otimizar o código.</span><span class="sxs-lookup"><span data-stu-id="cf60e-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf60e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf60e-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="cf60e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cf60e-105">Members</span></span>  
  
|<span data-ttu-id="cf60e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cf60e-106">Member</span></span>|<span data-ttu-id="cf60e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf60e-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="cf60e-108">Especifica que as referências de tipo e referências de membro devem ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="cf60e-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="cf60e-109">Esse é o valor padrão (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="cf60e-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="cf60e-110">Especifica que todos os itens mencionados devem ser convertidos em definições.</span><span class="sxs-lookup"><span data-stu-id="cf60e-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="cf60e-111">Especifica que nenhum item referenciado deve ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="cf60e-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="cf60e-112">Especifica que somente as referências de tipo devem ser convertidas para definições de tipo.</span><span class="sxs-lookup"><span data-stu-id="cf60e-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="cf60e-113">Especifica que somente as referências de membro devem ser convertidas em definições.</span><span class="sxs-lookup"><span data-stu-id="cf60e-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="cf60e-114">Ou seja, as referências de membro devem ser convertidas em definições de método ou definições de campo.</span><span class="sxs-lookup"><span data-stu-id="cf60e-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf60e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf60e-115">Requirements</span></span>  
 <span data-ttu-id="cf60e-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf60e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf60e-117">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="cf60e-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cf60e-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf60e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf60e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf60e-119">See Also</span></span>  
 [<span data-ttu-id="cf60e-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="cf60e-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
