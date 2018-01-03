---
title: AssemblyAttributesGoHere
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHere
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3363ac5bd53688cfaa667a57afce17b6b52b1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="4a82a-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="4a82a-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="4a82a-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="4a82a-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a82a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a82a-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="4a82a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a82a-105">Remarks</span></span>  
 <span data-ttu-id="4a82a-106">Referências a este tipo podem ser incorporadas dentro netmodules cujos fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a82a-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="4a82a-107">Ao criar um manifesto do assembly de um ou mais netmodules que contêm referências a esses tipos, ALink usa informações associadas a essas referências para emitir os atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="4a82a-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="4a82a-108">Como tal, esse tipo nunca é instanciado e referências a ele são usadas apenas como parte do processo de compilação e não servem para nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="4a82a-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="4a82a-109">Referências a esse tipo de indicam os atributos personalizados que não estão relacionadas à segurança e não use vários.</span><span class="sxs-lookup"><span data-stu-id="4a82a-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="4a82a-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados em <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="4a82a-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a82a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a82a-111">Requirements</span></span>  
 <span data-ttu-id="4a82a-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="4a82a-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a82a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a82a-113">See Also</span></span>  
 [<span data-ttu-id="4a82a-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="4a82a-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="4a82a-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="4a82a-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="4a82a-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="4a82a-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
