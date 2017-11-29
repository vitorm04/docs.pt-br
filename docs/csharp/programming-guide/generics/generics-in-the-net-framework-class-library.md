---
title: "Genéricos na biblioteca de classes .NET Framework (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], in .NET Framework class library
ms.assetid: afdd5477-6770-4686-8297-f58a4d749daf
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83ce8b8fe31a35e04c23c316ead5848aec79ec42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generics-in-the-net-framework-class-library-c-programming-guide"></a><span data-ttu-id="3c3e5-102">Genéricos na biblioteca de classes .NET Framework (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3c3e5-102">Generics in the .NET Framework Class Library (C# Programming Guide)</span></span>
<span data-ttu-id="3c3e5-103">A versão 2.0 da biblioteca de classes .NET Framework fornece um novo namespace, <xref:System.Collections.Generic>, que inclui várias classes de coleção genérica prontas para uso e interfaces associadas.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-103">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which includes several ready-to-use generic collection classes and associated interfaces.</span></span> <span data-ttu-id="3c3e5-104">Outros namespaces, como <xref:System>, também fornecem novas interfaces genéricas, como <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-104">Other namespaces, such as <xref:System>, also provide new generic interfaces such as <xref:System.IComparable%601>.</span></span> <span data-ttu-id="3c3e5-105">Essas classes e interfaces são mais eficientes e fortemente tipadas que as classes de coleção não genéricas fornecidas em versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-105">These classes and interfaces are more efficient and type-safe than the non-generic collection classes provided in earlier releases of the .NET Framework.</span></span> <span data-ttu-id="3c3e5-106">Antes de criar e implementar suas próprias classes de coleção personalizadas, considere se você pode usar ou derivar uma classe de uma das classes fornecidas na biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-106">Before designing and implementing your own custom collection classes, consider whether you can use or derive a class from one of the classes provided in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3e5-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c3e5-107">See Also</span></span>  
 [<span data-ttu-id="3c3e5-108">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3c3e5-108">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3c3e5-109">Quando Usar Coleções Genéricas</span><span class="sxs-lookup"><span data-stu-id="3c3e5-109">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
 [<span data-ttu-id="3c3e5-110">Coleções e Estruturas de Dados</span><span class="sxs-lookup"><span data-stu-id="3c3e5-110">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="3c3e5-111">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="3c3e5-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
