---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereS
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3506462aaf8d040126d979801460772b3cd47f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706278"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="52fda-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="52fda-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="52fda-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="52fda-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52fda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52fda-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="52fda-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="52fda-105">Remarks</span></span>  
 <span data-ttu-id="52fda-106">Referências a esse tipo podem ser incorporadas dentro dos netmodules cujas fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="52fda-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="52fda-107">Ao criar um manifesto do assembly de um ou mais dos netmodules que contêm referências a esses tipos, o ALink usa informações associadas a essas referências para emissão de atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="52fda-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="52fda-108">Como tal, esse tipo nunca é instanciado e as referências a ele são usadas apenas como parte do processo de compilação e nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="52fda-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="52fda-109">Referências a esse tipo de indicam os atributos personalizados que estão relacionados à segurança e não uso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="52fda-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="52fda-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados em <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="52fda-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52fda-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52fda-111">Requirements</span></span>  
 <span data-ttu-id="52fda-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="52fda-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52fda-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52fda-113">See also</span></span>
- [<span data-ttu-id="52fda-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="52fda-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="52fda-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="52fda-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="52fda-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="52fda-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
