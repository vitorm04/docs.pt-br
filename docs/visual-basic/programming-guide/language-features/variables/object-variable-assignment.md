---
title: Atribuição de variável do objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656052"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="31560-102">Atribuição de variável do objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31560-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="31560-103">Você pode usar uma instrução de atribuição normal para atribuir um objeto a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="31560-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="31560-104">Você pode atribuir uma expressão de objeto ou o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave, como o exemplo a seguir ilustra.</span><span class="sxs-lookup"><span data-stu-id="31560-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="31560-105">`Nothing` significa que não há nenhum objeto atualmente atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="31560-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="31560-106">Inicialização</span><span class="sxs-lookup"><span data-stu-id="31560-106">Initialization</span></span>  
 <span data-ttu-id="31560-107">Quando seu código começa a execução, o objeto variáveis são inicializadas como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="31560-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="31560-108">Aqueles cujas declarações incluem inicialização são reinicializados com os valores que você especificar quando as instruções de declaração são executadas.</span><span class="sxs-lookup"><span data-stu-id="31560-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="31560-109">Você pode incluir a inicialização na sua declaração usando o [novo](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="31560-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="31560-110">As seguintes instruções de declaração declaram variáveis de objeto `testUri` e `ver` e atribuir a objetos específicos a elas.</span><span class="sxs-lookup"><span data-stu-id="31560-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="31560-111">Cada uma usa um dos construtores sobrecarregados da classe apropriada para inicializar o objeto.</span><span class="sxs-lookup"><span data-stu-id="31560-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="31560-112">Dissociação</span><span class="sxs-lookup"><span data-stu-id="31560-112">Disassociation</span></span>  
 <span data-ttu-id="31560-113">Definindo uma variável de objeto `Nothing` interrompe a associação da variável com qualquer objeto específico.</span><span class="sxs-lookup"><span data-stu-id="31560-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="31560-114">Isso impede que você altere acidentalmente o objeto alterando a variável.</span><span class="sxs-lookup"><span data-stu-id="31560-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="31560-115">Ele também permite que você teste se a variável de objeto aponta para um objeto válido, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="31560-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="31560-116">Se o objeto que a variável se refere estiver em outro aplicativo, esse teste não pode determinar se esse aplicativo foi encerrada ou simplesmente invalidou o objeto.</span><span class="sxs-lookup"><span data-stu-id="31560-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="31560-117">Uma variável de objeto com um valor de `Nothing` também é chamado de um *referência nula*.</span><span class="sxs-lookup"><span data-stu-id="31560-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="31560-118">Instância atual</span><span class="sxs-lookup"><span data-stu-id="31560-118">Current Instance</span></span>  
 <span data-ttu-id="31560-119">O *atual instância* de um objeto é aquele no qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="31560-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="31560-120">Como todo o código é executado dentro de um procedimento, a instância atual é aquele no qual o procedimento foi chamado.</span><span class="sxs-lookup"><span data-stu-id="31560-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="31560-121">O `Me` palavra-chave atua como uma variável de objeto referindo-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="31560-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="31560-122">Se um procedimento não é [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ele pode usar o `Me` palavra-chave para obter um ponteiro para a instância atual.</span><span class="sxs-lookup"><span data-stu-id="31560-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="31560-123">Procedimentos compartilhados não podem ser associados uma instância específica de uma classe.</span><span class="sxs-lookup"><span data-stu-id="31560-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="31560-124">Usando `Me` é particularmente útil para passar a instância atual para um procedimento em outro módulo.</span><span class="sxs-lookup"><span data-stu-id="31560-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="31560-125">Por exemplo, suponha que você tem um número de documentos XML e deseja adicionar um texto padrão para todos eles.</span><span class="sxs-lookup"><span data-stu-id="31560-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="31560-126">O exemplo a seguir define um procedimento para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="31560-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="31560-127">Cada objeto de documento XML, em seguida, pode chamar o procedimento e passar sua instância atual como um argumento.</span><span class="sxs-lookup"><span data-stu-id="31560-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="31560-128">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="31560-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="31560-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31560-129">See Also</span></span>  
 [<span data-ttu-id="31560-130">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="31560-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="31560-131">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="31560-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="31560-132">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="31560-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="31560-133">Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31560-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="31560-134">Como fazer uma variável de objeto não se referir a nenhuma instância</span><span class="sxs-lookup"><span data-stu-id="31560-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [<span data-ttu-id="31560-135">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="31560-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
