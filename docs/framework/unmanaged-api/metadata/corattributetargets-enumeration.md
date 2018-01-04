---
title: "Enumeração CorAttributeTargets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAttributeTargets
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAttributeTargets
helpviewer_keywords: CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ce701c026b4e977c376b6e6f0f342b031634e38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="3f358-102">Enumeração CorAttributeTargets</span><span class="sxs-lookup"><span data-stu-id="3f358-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="3f358-103">Especifica os elementos do aplicativo no qual ele é válido para aplicar um atributo.</span><span class="sxs-lookup"><span data-stu-id="3f358-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f358-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f358-104">Syntax</span></span>  
  
```  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="3f358-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3f358-105">Members</span></span>  
  
|<span data-ttu-id="3f358-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3f358-106">Member</span></span>|<span data-ttu-id="3f358-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f358-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="3f358-108">O atributo pode ser aplicado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="3f358-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="3f358-109">Atributo pode ser aplicado a um módulo (. dll ou .exe) executável portátil.</span><span class="sxs-lookup"><span data-stu-id="3f358-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="3f358-110">O atributo pode ser aplicado a uma classe.</span><span class="sxs-lookup"><span data-stu-id="3f358-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="3f358-111">Atributo pode ser aplicado a uma estrutura; ou seja, um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="3f358-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="3f358-112">O atributo pode ser aplicado a uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="3f358-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="3f358-113">O atributo pode ser aplicado a um construtor.</span><span class="sxs-lookup"><span data-stu-id="3f358-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="3f358-114">O atributo pode ser aplicado a um método.</span><span class="sxs-lookup"><span data-stu-id="3f358-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="3f358-115">O atributo pode ser aplicado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f358-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="3f358-116">O atributo pode ser aplicado a um campo.</span><span class="sxs-lookup"><span data-stu-id="3f358-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="3f358-117">O atributo pode ser aplicado a um evento.</span><span class="sxs-lookup"><span data-stu-id="3f358-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="3f358-118">O atributo pode ser aplicado a uma interface.</span><span class="sxs-lookup"><span data-stu-id="3f358-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="3f358-119">O atributo pode ser aplicado a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3f358-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="3f358-120">O atributo pode ser aplicado a um delegado.</span><span class="sxs-lookup"><span data-stu-id="3f358-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="3f358-121">O atributo pode ser aplicado a um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="3f358-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="3f358-122">O atributo pode ser aplicado a qualquer elemento de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f358-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="3f358-123">Atributo pode ser aplicado a um membro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="3f358-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f358-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f358-124">Remarks</span></span>  
 <span data-ttu-id="3f358-125">O `CorAttributeTargets` valores de enumeração podem ser combinados com uma operação OR bit a bit para obter a combinação preferencial.</span><span class="sxs-lookup"><span data-stu-id="3f358-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="3f358-126">O `CorAttributeTargets` comparável ao gerenciado <xref:System.AttributeTargets?displayProperty=nameWithType> enumeração.</span><span class="sxs-lookup"><span data-stu-id="3f358-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f358-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f358-127">Requirements</span></span>  
 <span data-ttu-id="3f358-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f358-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f358-129">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="3f358-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3f358-130">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f358-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f358-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f358-131">See Also</span></span>  
 [<span data-ttu-id="3f358-132">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3f358-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
