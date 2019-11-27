---
title: Classe AssemblyAttributesGoHereM (System. Runtime. Compiladorservices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 15b9445aa3eabbd14541cfe5481bfb553c8c0347
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446623"
---
# <a name="assemblyattributesgoherem-class"></a><span data-ttu-id="95e4b-102">Classe AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="95e4b-102">AssemblyAttributesGoHereM Class</span></span>

<span data-ttu-id="95e4b-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="95e4b-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="95e4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95e4b-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a><span data-ttu-id="95e4b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="95e4b-105">Remarks</span></span>

<span data-ttu-id="95e4b-106">As referências a esse tipo podem ser inseridas dentro de netmodules cujas fontes contêm atributos personalizados de assembly.</span><span class="sxs-lookup"><span data-stu-id="95e4b-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="95e4b-107">Ao criar um manifesto do assembly a partir de um ou mais netmodules que contêm referências a esses tipos, o ALink usa informações anexadas a essas referências para emitir atributos personalizados reais.</span><span class="sxs-lookup"><span data-stu-id="95e4b-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="95e4b-108">Dessa forma, esse tipo nunca é instanciado e as referências a ele são usadas somente como parte do processo de compilação e não atendem a nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="95e4b-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="95e4b-109">Referências a este tipo indicam atributos personalizados que não são relacionados à segurança, mas que são de uso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="95e4b-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>

<span data-ttu-id="95e4b-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados no namespace <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="95e4b-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="95e4b-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95e4b-111">Requirements</span></span>

<span data-ttu-id="95e4b-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="95e4b-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="95e4b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95e4b-113">See also</span></span>

- [<span data-ttu-id="95e4b-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="95e4b-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="95e4b-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="95e4b-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="95e4b-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="95e4b-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
