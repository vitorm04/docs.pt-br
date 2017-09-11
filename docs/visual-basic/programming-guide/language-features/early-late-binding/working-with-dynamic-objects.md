---
title: "Trabalhando com objetos dinâmicos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d1e1c4f7338daad0f1101f6e886eba6c37316b0e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="5b6d1-102">Trabalhando com objetos dinâmicos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b6d1-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="5b6d1-103">Objetos dinâmicos oferecem uma outra maneira, que o `Object` tipo de ligação tardia a um objeto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5b6d1-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="5b6d1-104">Um objeto dinâmico expõe membros como métodos e propriedades em tempo de execução usando interfaces dinâmicas que são definidos na <xref:System.Dynamic>namespace.</xref:System.Dynamic></span><span class="sxs-lookup"><span data-stu-id="5b6d1-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="5b6d1-105">Você pode usar as classes de <xref:System.Dynamic>namespace para criar objetos de trabalhar com estruturas de dados que não correspondem a um formato ou tipo estático.</xref:System.Dynamic></span><span class="sxs-lookup"><span data-stu-id="5b6d1-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="5b6d1-106">Você também pode usar os objetos dinâmicos que são definidos em linguagens dinâmicas como o IronPython e IronRuby.</span><span class="sxs-lookup"><span data-stu-id="5b6d1-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="5b6d1-107">Para obter exemplos que mostram como criar objetos dinâmicos ou usar um objeto dinâmico definido em uma linguagem dinâmica, consulte [passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="5b6d1-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5b6d1-108">associa a objetos das linguagens dinâmicas, como o IronPython e IronRuby e runtime de linguagem dinâmico usando o <xref:System.Dynamic.IDynamicMetaObjectProvider>interface.</xref:System.Dynamic.IDynamicMetaObjectProvider></span><span class="sxs-lookup"><span data-stu-id="5b6d1-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="5b6d1-109">Exemplos de classes que implementam o `IDynamicMetaObjectProvider` interface são o <xref:System.Dynamic.DynamicObject>e <xref:System.Dynamic.ExpandoObject>classes.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="5b6d1-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="5b6d1-110">Se uma chamada de ligação tardia é feita em um objeto que implementa o `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] associa ao objeto dinâmico por meio dessa interface.</span><span class="sxs-lookup"><span data-stu-id="5b6d1-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="5b6d1-111">Se for feita uma chamada de ligação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface, ou se a chamada para o `IDynamicMetaObjectProvider` interface falhar, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] associa ao objeto usando os recursos de ligação tardia do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5b6d1-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6d1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b6d1-112">See Also</span></span>  
 <span data-ttu-id="5b6d1-113"><xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="5b6d1-113"><xref:System.Dynamic.DynamicObject></span></span>   
 <span data-ttu-id="5b6d1-114"><xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject></span><span class="sxs-lookup"><span data-stu-id="5b6d1-114"><xref:System.Dynamic.ExpandoObject></span></span>   
<span data-ttu-id="5b6d1-115"> [Passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5b6d1-115"> [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span></span>  
<span data-ttu-id="5b6d1-116"> [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="5b6d1-116"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
