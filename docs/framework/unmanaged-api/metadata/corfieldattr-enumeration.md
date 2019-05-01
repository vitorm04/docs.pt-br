---
title: Enumeração CorFieldAttr
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 432e202eb8db105e8d56d3d36cdc8001bac5320c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045936"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="79d60-102">Enumeração CorFieldAttr</span><span class="sxs-lookup"><span data-stu-id="79d60-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="79d60-103">Contém valores que descrevem os metadados sobre um campo.</span><span class="sxs-lookup"><span data-stu-id="79d60-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d60-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79d60-104">Syntax</span></span>  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="79d60-105">Membros</span><span class="sxs-lookup"><span data-stu-id="79d60-105">Members</span></span>  
  
|<span data-ttu-id="79d60-106">Membro</span><span class="sxs-lookup"><span data-stu-id="79d60-106">Member</span></span>|<span data-ttu-id="79d60-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="79d60-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="79d60-108">Especifica informações de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="79d60-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="79d60-109">Especifica que o campo não pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="79d60-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="79d60-110">Especifica que o campo é acessível somente por seu tipo pai.</span><span class="sxs-lookup"><span data-stu-id="79d60-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="79d60-111">Especifica que o campo pode ser acessado por classes derivadas em seu assembly.</span><span class="sxs-lookup"><span data-stu-id="79d60-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="79d60-112">Especifica que o campo pode ser acessado por todos os tipos em seu assembly.</span><span class="sxs-lookup"><span data-stu-id="79d60-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="79d60-113">Especifica que o campo é acessível somente por seu tipo e as classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="79d60-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="79d60-114">Especifica que o campo pode ser acessado por classes derivadas e por todos os tipos em seu assembly.</span><span class="sxs-lookup"><span data-stu-id="79d60-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="79d60-115">Especifica que o campo pode ser acessado por todos os tipos com visibilidade desse escopo.</span><span class="sxs-lookup"><span data-stu-id="79d60-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="79d60-116">Especifica que o campo é um membro de seu tipo, em vez de um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="79d60-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="79d60-117">Especifica que o campo não pode ser alterado depois que ele é inicializado.</span><span class="sxs-lookup"><span data-stu-id="79d60-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="79d60-118">Especifica que o valor do campo é uma constante de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="79d60-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="79d60-119">Especifica que o campo não é serializado quando seu tipo é remoto.</span><span class="sxs-lookup"><span data-stu-id="79d60-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="79d60-120">Especifica que o campo é especial, e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="79d60-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="79d60-121">Especifica que a implementação de campo é encaminhada por meio do PInvoke.</span><span class="sxs-lookup"><span data-stu-id="79d60-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="79d60-122">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="79d60-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="79d60-123">Especifica que os metadados do common language runtime APIs internas deve verificar a codificação de nome.</span><span class="sxs-lookup"><span data-stu-id="79d60-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="79d60-124">Especifica que o campo contém informações de marshaling.</span><span class="sxs-lookup"><span data-stu-id="79d60-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="79d60-125">Especifica que o campo tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="79d60-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="79d60-126">Especifica que o campo tem um endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="79d60-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79d60-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79d60-127">Requirements</span></span>  
 <span data-ttu-id="79d60-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79d60-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79d60-129">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="79d60-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="79d60-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79d60-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d60-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79d60-131">See also</span></span>

- [<span data-ttu-id="79d60-132">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="79d60-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
