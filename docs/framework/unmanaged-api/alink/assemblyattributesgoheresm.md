---
title: Classe AssemblyAttributesGoHereSM (System. Runtime. Compiladorservices)
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
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446604"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="8b597-102">Classe AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="8b597-102">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="8b597-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="8b597-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b597-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b597-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="8b597-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b597-105">Remarks</span></span>

<span data-ttu-id="8b597-106">As referências a esse tipo podem ser inseridas dentro de netmodules cujas fontes contêm atributos personalizados de assembly.</span><span class="sxs-lookup"><span data-stu-id="8b597-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="8b597-107">Ao criar um manifesto do assembly a partir de um ou mais netmodules que contêm referências a esses tipos, o ALink usa informações anexadas a essas referências para emitir atributos personalizados reais.</span><span class="sxs-lookup"><span data-stu-id="8b597-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="8b597-108">Dessa forma, esse tipo nunca é instanciado e as referências a ele são usadas somente como parte do processo de compilação e não atendem a nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="8b597-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="8b597-109">Referências a esse tipo indicam atributos personalizados que são relacionados à segurança e ao uso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="8b597-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="8b597-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados no namespace <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="8b597-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b597-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8b597-111">Requirements</span></span>

<span data-ttu-id="8b597-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="8b597-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="8b597-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b597-113">See also</span></span>

- [<span data-ttu-id="8b597-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="8b597-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="8b597-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="8b597-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="8b597-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="8b597-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
