---
title: Classe AssemblyAttributesGoHereSM (CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
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
ms.openlocfilehash: 01b156ed9c318e71a408ea10f2744911a85faedc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975362"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="e0dca-102">Classe AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="e0dca-102">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="e0dca-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="e0dca-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0dca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0dca-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="e0dca-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0dca-105">Remarks</span></span>

<span data-ttu-id="e0dca-106">Referências a esse tipo podem ser incorporadas dentro dos netmodules cujas fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0dca-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="e0dca-107">Ao criar um manifesto do assembly de um ou mais dos netmodules que contêm referências a esses tipos, o ALink usa informações associadas a essas referências para emissão de atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="e0dca-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="e0dca-108">Como tal, esse tipo nunca é instanciado e as referências a ele são usadas apenas como parte do processo de compilação e nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="e0dca-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="e0dca-109">Referências a esse tipo de indicam os atributos personalizados que estão relacionada e uso múltiplo de segurança.</span><span class="sxs-lookup"><span data-stu-id="e0dca-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="e0dca-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados no <xref:System.Runtime.CompilerServices> namespace.</span><span class="sxs-lookup"><span data-stu-id="e0dca-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0dca-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0dca-111">Requirements</span></span>

<span data-ttu-id="e0dca-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="e0dca-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="e0dca-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0dca-113">See also</span></span>

- [<span data-ttu-id="e0dca-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="e0dca-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="e0dca-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="e0dca-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="e0dca-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="e0dca-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
