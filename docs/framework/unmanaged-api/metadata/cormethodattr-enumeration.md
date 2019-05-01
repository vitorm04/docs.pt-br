---
title: Enumeração CorMethodAttr
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045520"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="82d69-102">Enumeração CorMethodAttr</span><span class="sxs-lookup"><span data-stu-id="82d69-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="82d69-103">Contém valores que descrevem os recursos de um método.</span><span class="sxs-lookup"><span data-stu-id="82d69-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82d69-104">Syntax</span></span>  
  
```  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="82d69-105">Membros</span><span class="sxs-lookup"><span data-stu-id="82d69-105">Members</span></span>  
  
|<span data-ttu-id="82d69-106">Membro</span><span class="sxs-lookup"><span data-stu-id="82d69-106">Member</span></span>|<span data-ttu-id="82d69-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="82d69-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="82d69-108">Especifica o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="82d69-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="82d69-109">Especifica que o membro não pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="82d69-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="82d69-110">Especifica que o membro é acessível somente por tipo de pai.</span><span class="sxs-lookup"><span data-stu-id="82d69-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="82d69-111">Especifica que o membro é acessado por subtipos somente nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="82d69-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="82d69-112">Especifica que o membro é acessível por qualquer pessoa no assembly.</span><span class="sxs-lookup"><span data-stu-id="82d69-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="82d69-113">Especifica que o membro é acessível somente por tipos e subtipos.</span><span class="sxs-lookup"><span data-stu-id="82d69-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="82d69-114">Especifica que o membro é acessado por classes derivadas e por outros tipos em seu assembly.</span><span class="sxs-lookup"><span data-stu-id="82d69-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="82d69-115">Especifica que o membro é acessado por todos os tipos com acesso ao escopo.</span><span class="sxs-lookup"><span data-stu-id="82d69-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="82d69-116">Especifica que o membro é definido como parte do tipo em vez de um membro de uma instância.</span><span class="sxs-lookup"><span data-stu-id="82d69-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="82d69-117">Especifica que o método não pode ser substituído.</span><span class="sxs-lookup"><span data-stu-id="82d69-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="82d69-118">Especifica que o método pode ser substituído.</span><span class="sxs-lookup"><span data-stu-id="82d69-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="82d69-119">Especifica que o método oculta por nome e assinatura, em vez de apenas por nome.</span><span class="sxs-lookup"><span data-stu-id="82d69-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="82d69-120">Especifica o layout da tabela virtual.</span><span class="sxs-lookup"><span data-stu-id="82d69-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="82d69-121">Especifica que o slot utilizado para esse método na tabela virtual ser reutilizadas.</span><span class="sxs-lookup"><span data-stu-id="82d69-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="82d69-122">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="82d69-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="82d69-123">Especifica que o método sempre obtém um novo slot na tabela virtual.</span><span class="sxs-lookup"><span data-stu-id="82d69-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="82d69-124">Especifica que o método pode ser substituído pelos mesmos tipos aos quais ele está visível.</span><span class="sxs-lookup"><span data-stu-id="82d69-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="82d69-125">Especifica que o método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="82d69-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="82d69-126">Especifica que o método é especial, e que seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="82d69-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="82d69-127">Especifica que a implementação do método é encaminhada usando PInvoke.</span><span class="sxs-lookup"><span data-stu-id="82d69-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="82d69-128">Especifica que o método é um método gerenciado exportado para o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="82d69-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="82d69-129">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="82d69-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="82d69-130">Especifica que o common language runtime deve verificar a codificação do nome do método.</span><span class="sxs-lookup"><span data-stu-id="82d69-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="82d69-131">Especifica que o método tem segurança associada a ele.</span><span class="sxs-lookup"><span data-stu-id="82d69-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="82d69-132">Especifica que o método chama outro método que contém o código de segurança.</span><span class="sxs-lookup"><span data-stu-id="82d69-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82d69-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82d69-133">Requirements</span></span>  
 <span data-ttu-id="82d69-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d69-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d69-135">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="82d69-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="82d69-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82d69-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d69-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82d69-137">See also</span></span>

- [<span data-ttu-id="82d69-138">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="82d69-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
