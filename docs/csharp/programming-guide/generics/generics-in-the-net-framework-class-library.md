---
title: "Genéricos na biblioteca de classes .NET Framework (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], in .NET Framework class library
ms.assetid: afdd5477-6770-4686-8297-f58a4d749daf
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f3d5f15c92031301b68c6a702cf8d6b135cca36d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="generics-in-the-net-framework-class-library-c-programming-guide"></a><span data-ttu-id="2f79d-102">Genéricos na biblioteca de classes .NET Framework (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2f79d-102">Generics in the .NET Framework Class Library (C# Programming Guide)</span></span>
<span data-ttu-id="2f79d-103">A versão 2.0 da biblioteca de classes .NET Framework fornece um novo namespace, <xref:System.Collections.Generic>, que inclui várias classes de coleção genérica prontas para uso e interfaces associadas.</span><span class="sxs-lookup"><span data-stu-id="2f79d-103">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which includes several ready-to-use generic collection classes and associated interfaces.</span></span> <span data-ttu-id="2f79d-104">Outros namespaces, como <xref:System>, também fornecem novas interfaces genéricas, como <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="2f79d-104">Other namespaces, such as <xref:System>, also provide new generic interfaces such as <xref:System.IComparable%601>.</span></span> <span data-ttu-id="2f79d-105">Essas classes e interfaces são mais eficientes e fortemente tipadas que as classes de coleção não genéricas fornecidas em versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f79d-105">These classes and interfaces are more efficient and type-safe than the non-generic collection classes provided in earlier releases of the .NET Framework.</span></span> <span data-ttu-id="2f79d-106">Antes de criar e implementar suas próprias classes de coleção personalizadas, considere se você pode usar ou derivar uma classe de uma das classes fornecidas na biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f79d-106">Before designing and implementing your own custom collection classes, consider whether you can use or derive a class from one of the classes provided in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f79d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f79d-107">See Also</span></span>  
 <span data-ttu-id="2f79d-108">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2f79d-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2f79d-109">[Quando usar coleções genéricas](../../../standard/collections/when-to-use-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="2f79d-109">[When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md) </span></span>  
 <span data-ttu-id="2f79d-110">[Coleções e estruturas de dados](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="2f79d-110">[Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
 [<span data-ttu-id="2f79d-111">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="2f79d-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)

