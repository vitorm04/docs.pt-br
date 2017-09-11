---
title: "Atribuição de variável (Visual Basic) do objeto | Documentos do Microsoft"
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
- Nothing keyword, object variable assignment
- object variables, initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables, assigning
- variables [Visual Basic], object variables
- current instance, defined
- variables [Visual Basic], assigning
- assignment statements, object variable assignment
- Me keyword, as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: 19
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
ms.openlocfilehash: cadd71466ff0abafebbfceecb33e53c27b6006ab
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="39628-102">Atribuição de variável do objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39628-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="39628-103">Você pode usar uma instrução de atribuição normal para atribuir um objeto a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="39628-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="39628-104">Você pode atribuir uma expressão de objeto ou o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave, como o exemplo a seguir ilustra.</span><span class="sxs-lookup"><span data-stu-id="39628-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="39628-105">`Nothing`significa que não há nenhum objeto atualmente atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="39628-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="39628-106">Inicialização</span><span class="sxs-lookup"><span data-stu-id="39628-106">Initialization</span></span>  
 <span data-ttu-id="39628-107">Quando seu código começa a executar, seu objeto variáveis são inicializadas como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="39628-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="39628-108">Aqueles cujas declarações incluem inicialização são reinicializadas para os valores que você especifica quando as instruções de declaração são executadas.</span><span class="sxs-lookup"><span data-stu-id="39628-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="39628-109">Você pode incluir a inicialização na sua declaração usando o [novo](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="39628-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="39628-110">As seguintes instruções de declaração declaram variáveis de objeto `testUri` e `ver` e atribuem objetos específicos a elas.</span><span class="sxs-lookup"><span data-stu-id="39628-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="39628-111">Cada uma usa um dos construtores sobrecarregados da classe apropriada para inicializar o objeto.</span><span class="sxs-lookup"><span data-stu-id="39628-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="39628-112">Dissociação</span><span class="sxs-lookup"><span data-stu-id="39628-112">Disassociation</span></span>  
 <span data-ttu-id="39628-113">Definindo uma variável de objeto `Nothing` interrompe a associação da variável com qualquer objeto específico.</span><span class="sxs-lookup"><span data-stu-id="39628-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="39628-114">Isso impede que você altere acidentalmente o objeto alterando a variável.</span><span class="sxs-lookup"><span data-stu-id="39628-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="39628-115">Ele também permite testar se a variável de objeto aponta para um objeto válido, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="39628-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="39628-116">Se o objeto que sua variável se refere estiver em outro aplicativo, esse teste não pode determinar se esse aplicativo foi finalizado ou simplesmente invalidou o objeto.</span><span class="sxs-lookup"><span data-stu-id="39628-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="39628-117">Uma variável de objeto com um valor de `Nothing` também é chamado de um *nulo de referência*.</span><span class="sxs-lookup"><span data-stu-id="39628-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="39628-118">Instância atual</span><span class="sxs-lookup"><span data-stu-id="39628-118">Current Instance</span></span>  
 <span data-ttu-id="39628-119">O *atual instância* de um objeto é aquele no qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="39628-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="39628-120">Como todo o código é executado dentro de um procedimento, a instância atual é aquele no qual o procedimento foi chamado.</span><span class="sxs-lookup"><span data-stu-id="39628-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="39628-121">O `Me` palavra-chave atua como uma variável de objeto referindo-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="39628-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="39628-122">Se um procedimento não é [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), pode usar o `Me` palavra-chave para obter um ponteiro para a instância atual.</span><span class="sxs-lookup"><span data-stu-id="39628-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="39628-123">Procedimentos compartilhados não podem ser associados uma instância específica de uma classe.</span><span class="sxs-lookup"><span data-stu-id="39628-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="39628-124">Usando `Me` é particularmente útil para passar a instância atual para um procedimento em outro módulo.</span><span class="sxs-lookup"><span data-stu-id="39628-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="39628-125">Por exemplo, suponha que você tem um número de documentos XML e deseja adicionar um texto padrão para todos eles.</span><span class="sxs-lookup"><span data-stu-id="39628-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="39628-126">O exemplo a seguir define um procedimento para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="39628-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="39628-127">Cada objeto de documento XML poderia, em seguida, chame o procedimento e passar sua instância atual como um argumento.</span><span class="sxs-lookup"><span data-stu-id="39628-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="39628-128">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="39628-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="39628-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39628-129">See Also</span></span>  
 <span data-ttu-id="39628-130">[Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="39628-130">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="39628-131"> [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="39628-131"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="39628-132"> [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="39628-132"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="39628-133"> [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md) </span><span class="sxs-lookup"><span data-stu-id="39628-133"> [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md) </span></span>  
<span data-ttu-id="39628-134"> [Como: fazer um objeto variável não se referir a qualquer instância](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md) </span><span class="sxs-lookup"><span data-stu-id="39628-134"> [How to: Make an Object Variable Not Refer to Any Instance](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md) </span></span>  
<span data-ttu-id="39628-135"> [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="39628-135"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>
