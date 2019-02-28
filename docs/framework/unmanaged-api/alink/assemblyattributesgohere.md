---
title: Classe AssemblyAttributesGoHere (CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571c2f6723e827a1b385f77724c33703ae970ae3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968108"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="84c3f-102">Classe AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="84c3f-102">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="84c3f-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="84c3f-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="84c3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84c3f-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="84c3f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="84c3f-105">Remarks</span></span>

<span data-ttu-id="84c3f-106">Referências a esse tipo podem ser incorporadas dentro dos netmodules cujas fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="84c3f-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="84c3f-107">Ao criar um manifesto do assembly de um ou mais dos netmodules que contêm referências a esses tipos, o ALink usa informações associadas a essas referências para emissão de atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="84c3f-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="84c3f-108">Como tal, esse tipo nunca é instanciado e as referências a ele são usadas apenas como parte do processo de compilação e nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="84c3f-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="84c3f-109">Referências a esse tipo de indicam os atributos personalizados que não estão relacionadas à segurança e não uso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="84c3f-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="84c3f-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados no <xref:System.Runtime.CompilerServices> namespace.</span><span class="sxs-lookup"><span data-stu-id="84c3f-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="84c3f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84c3f-111">Requirements</span></span>

<span data-ttu-id="84c3f-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="84c3f-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="84c3f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84c3f-113">See also</span></span>

- [<span data-ttu-id="84c3f-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="84c3f-114">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="84c3f-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="84c3f-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="84c3f-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="84c3f-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
