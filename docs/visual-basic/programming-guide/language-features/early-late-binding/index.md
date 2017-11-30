---
title: "Associação antecipada e tardia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aceffe59fb6043b3089621b9a3f95b0425f9a522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="83217-102">Associação antecipada e tardia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83217-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="83217-103">O compilador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] executa um processo chamado `binding` quando um objeto é atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="83217-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="83217-104">Um objeto é *associado inicialmente* quando ele é atribuído a uma variável declarada como de um tipo de objeto específico.</span><span class="sxs-lookup"><span data-stu-id="83217-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="83217-105">Os objetos de associação inicial permitem que o compilador aloque memória e execute outras otimizações antes que um aplicativo seja executado.</span><span class="sxs-lookup"><span data-stu-id="83217-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="83217-106">Por exemplo, o seguinte fragmento de código declara que uma variável é do tipo <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="83217-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <span data-ttu-id="83217-107">Uma vez que <xref:System.IO.FileStream> é um tipo de objeto específico, a instância atribuída a `FS` é associada no início.</span><span class="sxs-lookup"><span data-stu-id="83217-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="83217-108">Por outro lado, um objeto *associado tardiamente* quando ele é atribuído a uma variável declarada para ser do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="83217-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="83217-109">Objetos desse tipo podem conter referências a qualquer objeto, mas têm muitas das vantagens de objetos de associação inicial.</span><span class="sxs-lookup"><span data-stu-id="83217-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="83217-110">Por exemplo, o fragmento de código a seguir declara uma variável de objeto para conter um objeto retornado pela função `CreateObject`:</span><span class="sxs-lookup"><span data-stu-id="83217-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="83217-111">Vantagens da associação inicial</span><span class="sxs-lookup"><span data-stu-id="83217-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="83217-112">Você deve usar objetos associação inicial sempre que possível, pois eles permitem que o compilador faça otimizações importantes que resultam em aplicativos mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="83217-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="83217-113">Os objetos de associação inicial são significativamente mais rápidos do que objetos de associação tardia e tornam seu código mais fácil de ler e manter informando exatamente quais tipos de objetos estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="83217-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="83217-114">Outra vantagem da associação inicial é que ela permite que recursos úteis, como a conclusão de código automática e ajuda dinâmica, pois o IDE (ambiente de desenvolvimento integrado) [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] pode determinar exatamente com qual tipo de objeto você está trabalhando conforme você edita o código.</span><span class="sxs-lookup"><span data-stu-id="83217-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="83217-115">A associação inicial reduz o número e a gravidade dos erros em tempo de execução porque ela permite que o compilador relate erros quando um programa é compilado.</span><span class="sxs-lookup"><span data-stu-id="83217-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83217-116">A associação tardia só pode ser usada para acessar membros de tipo que são declarados como `Public`.</span><span class="sxs-lookup"><span data-stu-id="83217-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="83217-117">Acessando membros declarados como `Friend` ou `Protected Friend` resulta em um erro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83217-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83217-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83217-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [<span data-ttu-id="83217-119">Tempo de vida do objeto: como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="83217-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="83217-120">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="83217-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
