---
title: AssemblyAttributesGoHereM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 075f0ce7001573bb4e61a3e059e699d15275ea0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403182"
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="6bc17-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="6bc17-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="6bc17-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="6bc17-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bc17-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="6bc17-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6bc17-105">Remarks</span></span>  
 <span data-ttu-id="6bc17-106">Referências a este tipo podem ser incorporadas dentro netmodules cujos fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="6bc17-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="6bc17-107">Ao criar um manifesto do assembly de um ou mais netmodules que contêm referências a esses tipos, ALink usa informações associadas a essas referências para emitir os atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="6bc17-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="6bc17-108">Como tal, esse tipo nunca é instanciado e referências a ele são usadas apenas como parte do processo de compilação e não servem para nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="6bc17-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="6bc17-109">Referências a esse tipo de indicam os atributos personalizados que não estão relacionadas à segurança, mas use vários.</span><span class="sxs-lookup"><span data-stu-id="6bc17-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="6bc17-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados em <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="6bc17-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bc17-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bc17-111">Requirements</span></span>  
 <span data-ttu-id="6bc17-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="6bc17-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc17-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc17-113">See Also</span></span>  
 [<span data-ttu-id="6bc17-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="6bc17-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="6bc17-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="6bc17-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="6bc17-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="6bc17-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
