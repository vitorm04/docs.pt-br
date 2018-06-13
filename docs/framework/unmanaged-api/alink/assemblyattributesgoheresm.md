---
title: AssemblyAttributesGoHereSM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereSM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bed903c7380bc73601f03a83d2c637ef34d9b9e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405208"
---
# <a name="assemblyattributesgoheresm"></a><span data-ttu-id="3b8e2-102">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="3b8e2-102">AssemblyAttributesGoHereSM</span></span>
<span data-ttu-id="3b8e2-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="3b8e2-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b8e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b8e2-104">Syntax</span></span>  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b8e2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b8e2-105">Remarks</span></span>  
 <span data-ttu-id="3b8e2-106">Referências a este tipo podem ser incorporadas dentro netmodules cujos fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="3b8e2-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="3b8e2-107">Ao criar um manifesto do assembly de um ou mais netmodules que contêm referências a esses tipos, ALink usa informações associadas a essas referências para emitir os atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="3b8e2-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="3b8e2-108">Como tal, esse tipo nunca é instanciado e referências a ele são usadas apenas como parte do processo de compilação e não servem para nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="3b8e2-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="3b8e2-109">Referências a este tipo indicam atributos personalizados que são de segurança relacionada e usar vários.</span><span class="sxs-lookup"><span data-stu-id="3b8e2-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>  
  
 <span data-ttu-id="3b8e2-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados em <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="3b8e2-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b8e2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b8e2-111">Requirements</span></span>  
 <span data-ttu-id="3b8e2-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="3b8e2-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b8e2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b8e2-113">See Also</span></span>  
 [<span data-ttu-id="3b8e2-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="3b8e2-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="3b8e2-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="3b8e2-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="3b8e2-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="3b8e2-116">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
