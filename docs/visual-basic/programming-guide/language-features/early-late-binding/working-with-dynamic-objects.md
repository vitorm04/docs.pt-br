---
title: "Trabalhando com objetos dinâmicos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="cf622-102">Trabalhando com objetos dinâmicos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf622-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="cf622-103">Objetos dinâmicos oferecem uma outra maneira, que o `Object` tipo de associação tardia a um objeto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cf622-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="cf622-104">Um objeto dinâmico expõe membros, como métodos e propriedades em tempo de execução usando interfaces dinâmicos que são definidas no <xref:System.Dynamic> namespace.</span><span class="sxs-lookup"><span data-stu-id="cf622-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="cf622-105">Você pode usar as classes de <xref:System.Dynamic> namespace para criar objetos de trabalhar com estruturas de dados que não correspondem a um formato ou tipo estático.</span><span class="sxs-lookup"><span data-stu-id="cf622-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="cf622-106">Você também pode usar os objetos dinâmicos que são definidos em linguagens dinâmicas, como o IronPython e IronRuby.</span><span class="sxs-lookup"><span data-stu-id="cf622-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="cf622-107">Para obter exemplos que mostram como criar objetos dinâmicos ou usar um objeto dinâmico definido em linguagem dinâmica, consulte [passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.</span><span class="sxs-lookup"><span data-stu-id="cf622-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="cf622-108">associa a objetos do tempo de execução de linguagem dinâmica e linguagens dinâmicas, como o IronPython e IronRuby usando o <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span><span class="sxs-lookup"><span data-stu-id="cf622-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="cf622-109">Exemplos de classes que implementam o `IDynamicMetaObjectProvider` interface são o <xref:System.Dynamic.DynamicObject> e <xref:System.Dynamic.ExpandoObject> classes.</span><span class="sxs-lookup"><span data-stu-id="cf622-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="cf622-110">Se for feita uma chamada de associação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] associa ao objeto dinâmico usando essa interface.</span><span class="sxs-lookup"><span data-stu-id="cf622-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="cf622-111">Se for feita uma chamada de associação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface, ou se a chamada para o `IDynamicMetaObjectProvider` interface falhar, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] associa ao objeto, usando os recursos de associação tardia do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cf622-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf622-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf622-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="cf622-113">Passo a passo: Criando e usando objetos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="cf622-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="cf622-114">Associação Antecipada e Tardia</span><span class="sxs-lookup"><span data-stu-id="cf622-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
