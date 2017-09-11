---
title: "Declaração de variável (Visual Basic) do objeto | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- early binding
- declarations, class
- classes [Visual Basic], declaring
- binding, late and early
- object variables, declaring
- variables [Visual Basic], object
- declaring variables, object variables
- declaring classes
- late binding
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: 33
author: stevehoag
ms.author: shoag
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7dca56d1f5f6fff7cb758c9a1bfe80b30a2b4318
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="af04c-102">Declaração de variável do objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af04c-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="af04c-103">Você usa uma declaração comum para declarar uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="af04c-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="af04c-104">Para o tipo de dados, você especificar `Object` (ou seja, o [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ou uma classe mais específica da qual o objeto deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="af04c-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="af04c-105">Declarar uma variável como `Object` é o mesmo que declará-la como <xref:System.Object?displayProperty=fullName>.</xref:System.Object?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="af04c-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="af04c-106">Quando você declara uma variável com uma classe de objeto específica, ele pode acessar todos os métodos e propriedades expostas pela classe e as classes do qual ele herda.</span><span class="sxs-lookup"><span data-stu-id="af04c-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="af04c-107">Se você declarar a variável com <xref:System.Object>, ele pode acessar somente os membros do <xref:System.Object>de classe, a menos que você ative `Option Strict Off` para permitir a ligação tardia.</xref:System.Object> </xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="af04c-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="af04c-108">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="af04c-108">Declaration Syntax</span></span>  
 <span data-ttu-id="af04c-109">Use a seguinte sintaxe para declarar uma variável de objeto:</span><span class="sxs-lookup"><span data-stu-id="af04c-109">Use the following syntax to declare an object variable:</span></span>  
  
```  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="af04c-110">Você também pode especificar [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [particular](../../../../visual-basic/language-reference/modifiers/private.md), [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ou [estático](../../../../visual-basic/language-reference/modifiers/static.md) na declaração.</span><span class="sxs-lookup"><span data-stu-id="af04c-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="af04c-111">As seguintes declarações de exemplo são válidas:</span><span class="sxs-lookup"><span data-stu-id="af04c-111">The following example declarations are valid:</span></span>  
  
```  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="af04c-112">Associação tardia ou associação inicial</span><span class="sxs-lookup"><span data-stu-id="af04c-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="af04c-113">Às vezes, a classe específica é desconhecida até que seu código é executado.</span><span class="sxs-lookup"><span data-stu-id="af04c-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="af04c-114">Nesse caso, você deve declarar a variável de objeto com o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="af04c-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="af04c-115">Isso cria uma referência geral para qualquer tipo de objeto, e a classe específica é atribuída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="af04c-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="af04c-116">Isso é chamado de *ligação tardia*.</span><span class="sxs-lookup"><span data-stu-id="af04c-116">This is called *late binding*.</span></span> <span data-ttu-id="af04c-117">A associação tardia exige tempo adicional de execução.</span><span class="sxs-lookup"><span data-stu-id="af04c-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="af04c-118">Ela também limita seu código para os métodos e propriedades da classe que mais recentemente atribuídos a ele.</span><span class="sxs-lookup"><span data-stu-id="af04c-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="af04c-119">Isso pode causar erros de tempo de execução se seu código tentar acessar membros de uma classe diferente.</span><span class="sxs-lookup"><span data-stu-id="af04c-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="af04c-120">Quando você conhece a classe específica em tempo de compilação, você deve declarar a variável de objeto para ser daquela classe.</span><span class="sxs-lookup"><span data-stu-id="af04c-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="af04c-121">Isso é chamado de *vinculação inicial*.</span><span class="sxs-lookup"><span data-stu-id="af04c-121">This is called *early binding*.</span></span> <span data-ttu-id="af04c-122">Associação antecipada melhora o desempenho e garante a seu código de acesso a todos os métodos e propriedades da classe específica.</span><span class="sxs-lookup"><span data-stu-id="af04c-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="af04c-123">Nas declarações de exemplo anteriores, se a variável `objA` usa somente objetos da classe <xref:System.Windows.Forms.Label?displayProperty=fullName>, você deve especificar `As System.Windows.Forms.Label` na sua declaração.</xref:System.Windows.Forms.Label?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="af04c-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=fullName>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="af04c-124">Vantagens da associação inicial</span><span class="sxs-lookup"><span data-stu-id="af04c-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="af04c-125">Declarar uma variável de objeto como uma classe específica dá várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="af04c-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
-   <span data-ttu-id="af04c-126">Verificação de tipo automática</span><span class="sxs-lookup"><span data-stu-id="af04c-126">Automatic type checking</span></span>  
  
-   <span data-ttu-id="af04c-127">A garantia de acesso a todos os membros da classe específica</span><span class="sxs-lookup"><span data-stu-id="af04c-127">Guaranteed access to all members of the specific class</span></span>  
  
-   <span data-ttu-id="af04c-128">Suporte do Microsoft IntelliSense no Editor de códigos</span><span class="sxs-lookup"><span data-stu-id="af04c-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
-   <span data-ttu-id="af04c-129">Melhor legibilidade do seu código</span><span class="sxs-lookup"><span data-stu-id="af04c-129">Improved readability of your code</span></span>  
  
-   <span data-ttu-id="af04c-130">Menos erros no seu código</span><span class="sxs-lookup"><span data-stu-id="af04c-130">Fewer errors in your code</span></span>  
  
-   <span data-ttu-id="af04c-131">Erros pegos em tempo de compilação, em vez de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="af04c-131">Errors caught at compile time rather than run time</span></span>  
  
-   <span data-ttu-id="af04c-132">Execução de código mais rápida</span><span class="sxs-lookup"><span data-stu-id="af04c-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="af04c-133">Acesso aos membros das variáveis objeto</span><span class="sxs-lookup"><span data-stu-id="af04c-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="af04c-134">Quando `Option Strict` está ativado `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual foi declarada.</span><span class="sxs-lookup"><span data-stu-id="af04c-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="af04c-135">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="af04c-135">The following example illustrates this.</span></span>  
  
```  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="af04c-136">Neste exemplo, `p` pode usar somente os membros do <xref:System.Object>classe em si, que não inclui o `Left` propriedade.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="af04c-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="af04c-137">Por outro lado, `q` foi declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label>classe o <xref:System.Windows.Forms>namespace.</xref:System.Windows.Forms> </xref:System.Windows.Forms.Label> </xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="af04c-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="af04c-138">Flexibilidade de variáveis de objeto</span><span class="sxs-lookup"><span data-stu-id="af04c-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="af04c-139">Ao trabalhar com objetos em uma hierarquia de herança, você tem a opção de qual classe usar para declarar as variáveis de objeto.</span><span class="sxs-lookup"><span data-stu-id="af04c-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="af04c-140">Fazendo a escolha, você deve equilibrar a flexibilidade de atribuição de objeto contra o acesso a membros de uma classe.</span><span class="sxs-lookup"><span data-stu-id="af04c-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="af04c-141">Por exemplo, considere a hierarquia de herança que leva para o <xref:System.Windows.Forms.Form?displayProperty=fullName>classe:</xref:System.Windows.Forms.Form?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="af04c-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=fullName> class:</span></span>  
  
 <span data-ttu-id="af04c-142"><xref:System.Object></xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="af04c-142"><xref:System.Object></span></span>  
  
 <span data-ttu-id="af04c-143">``<xref:System.ComponentModel.Component></xref:System.ComponentModel.Component></span><span class="sxs-lookup"><span data-stu-id="af04c-143">`` <xref:System.ComponentModel.Component></span></span>  
  
 <span data-ttu-id="af04c-144">``<xref:System.Windows.Forms.Control></xref:System.Windows.Forms.Control></span><span class="sxs-lookup"><span data-stu-id="af04c-144">`` <xref:System.Windows.Forms.Control></span></span>  
  
 <span data-ttu-id="af04c-145">``<xref:System.Windows.Forms.ScrollableControl></xref:System.Windows.Forms.ScrollableControl></span><span class="sxs-lookup"><span data-stu-id="af04c-145">`` <xref:System.Windows.Forms.ScrollableControl></span></span>  
  
 <span data-ttu-id="af04c-146">``<xref:System.Windows.Forms.ContainerControl></xref:System.Windows.Forms.ContainerControl></span><span class="sxs-lookup"><span data-stu-id="af04c-146">`` <xref:System.Windows.Forms.ContainerControl></span></span>  
  
 <span data-ttu-id="af04c-147">``<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="af04c-147">`` <xref:System.Windows.Forms.Form></span></span>  
  
 <span data-ttu-id="af04c-148">Suponha que seu aplicativo define uma classe de formulário chamada `specialForm`, que herda da classe <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="af04c-148">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="af04c-149">Você pode declarar uma variável de objeto refere-se especificamente ao `specialForm`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="af04c-149">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
<span data-ttu-id="af04c-150"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="af04c-150"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="af04c-151">A declaração no exemplo anterior limita a variável `nextForm` para objetos da classe `specialForm`, mas também deixa todos os métodos e propriedades de `specialForm` para `nextForm`, assim como todos os membros de todas as classes do qual `specialForm` herda.</span><span class="sxs-lookup"><span data-stu-id="af04c-151">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="af04c-152">Você pode fazer uma variável de objeto mais geral declarando-a para ser do tipo <xref:System.Windows.Forms.Form>, como mostra o exemplo a seguir.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="af04c-152">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
<span data-ttu-id="af04c-153"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="af04c-153"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="af04c-154">A declaração no exemplo anterior permite designar qualquer formulário em seu aplicativo para `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="af04c-154">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="af04c-155">No entanto, embora `anyForm` pode acessar todos os membros da classe <xref:System.Windows.Forms.Form>, ele não pode usar qualquer um dos métodos adicionais ou propriedades definidas para formulários específicos como `specialForm`.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="af04c-155">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="af04c-156">Todos os membros de uma classe base estão disponíveis para as classes derivadas, mas os membros adicionais de uma classe derivada não estão disponíveis para a classe base.</span><span class="sxs-lookup"><span data-stu-id="af04c-156">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af04c-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af04c-157">See Also</span></span>  
 <span data-ttu-id="af04c-158">[Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-158">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="af04c-159"> [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-159"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="af04c-160"> [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-160"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="af04c-161"> [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-161"> [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md) </span></span>  
<span data-ttu-id="af04c-162"> [Como: acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-162"> [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span></span>  
<span data-ttu-id="af04c-163"> [Novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-163"> [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="af04c-164"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="af04c-164"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="af04c-165"> [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="af04c-165"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>
