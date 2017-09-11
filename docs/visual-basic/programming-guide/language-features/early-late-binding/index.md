---
title: "Associação antecipada e tardia (Visual Basic)"
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
- early binding
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding, Visual Basic compiler
- binding, late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding
- late binding, Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 66a34580417fb8b4a814b237ec36ffe700b1b30a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="65096-102">Associação antecipada e tardia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65096-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="65096-103">O compilador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] executa um processo chamado `binding` quando um objeto é atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="65096-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="65096-104">Um objeto é *associado inicialmente* quando ele é atribuído a uma variável declarada como de um tipo de objeto específico.</span><span class="sxs-lookup"><span data-stu-id="65096-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="65096-105">Os objetos de associação inicial permitem que o compilador aloque memória e execute outras otimizações antes que um aplicativo seja executado.</span><span class="sxs-lookup"><span data-stu-id="65096-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="65096-106">Por exemplo, o seguinte fragmento de código declara que uma variável é do tipo <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="65096-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 <span data-ttu-id="65096-107">[!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="65096-107">[!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]</span></span>  
  
 <span data-ttu-id="65096-108">Uma vez que <xref:System.IO.FileStream> é um tipo de objeto específico, a instância atribuída a `FS` é associada no início.</span><span class="sxs-lookup"><span data-stu-id="65096-108">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="65096-109">Por outro lado, um objeto *associado tardiamente* quando ele é atribuído a uma variável declarada para ser do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="65096-109">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="65096-110">Objetos desse tipo podem conter referências a qualquer objeto, mas têm muitas das vantagens de objetos de associação inicial.</span><span class="sxs-lookup"><span data-stu-id="65096-110">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="65096-111">Por exemplo, o fragmento de código a seguir declara uma variável de objeto para conter um objeto retornado pela função `CreateObject`:</span><span class="sxs-lookup"><span data-stu-id="65096-111">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 <span data-ttu-id="65096-112">[!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="65096-112">[!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]</span></span>  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="65096-113">Vantagens da associação inicial</span><span class="sxs-lookup"><span data-stu-id="65096-113">Advantages of Early Binding</span></span>  
 <span data-ttu-id="65096-114">Você deve usar objetos associação inicial sempre que possível, pois eles permitem que o compilador faça otimizações importantes que resultam em aplicativos mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="65096-114">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="65096-115">Os objetos de associação inicial são significativamente mais rápidos do que objetos de associação tardia e tornam seu código mais fácil de ler e manter informando exatamente quais tipos de objetos estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="65096-115">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="65096-116">Outra vantagem da associação inicial é que ela permite que recursos úteis, como a conclusão de código automática e ajuda dinâmica, pois o IDE (ambiente de desenvolvimento integrado) [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] pode determinar exatamente com qual tipo de objeto você está trabalhando conforme você edita o código.</span><span class="sxs-lookup"><span data-stu-id="65096-116">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="65096-117">A associação inicial reduz o número e a gravidade dos erros em tempo de execução porque ela permite que o compilador relate erros quando um programa é compilado.</span><span class="sxs-lookup"><span data-stu-id="65096-117">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65096-118">A associação tardia só pode ser usada para acessar membros de tipo que são declarados como `Public`.</span><span class="sxs-lookup"><span data-stu-id="65096-118">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="65096-119">Acessando membros declarados como `Friend` ou `Protected Friend` resulta em um erro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="65096-119">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65096-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65096-120">See Also</span></span>  
 <span data-ttu-id="65096-121"><xref:Microsoft.VisualBasic.Interaction.CreateObject%2A></span><span class="sxs-lookup"><span data-stu-id="65096-121"><xref:Microsoft.VisualBasic.Interaction.CreateObject%2A></span></span>   
 <span data-ttu-id="65096-122">[Tempo de vida do objeto: como os objetos são criados e destruídos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md) </span><span class="sxs-lookup"><span data-stu-id="65096-122">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md) </span></span>  
 [<span data-ttu-id="65096-123">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="65096-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

