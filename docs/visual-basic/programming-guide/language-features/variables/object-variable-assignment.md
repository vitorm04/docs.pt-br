---
title: Atribuição de variável do objeto
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
ms.openlocfilehash: 9ae1a307e8c886166d516140b7f100a411cedcfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410368"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="f4b93-102">Atribuição de variável do objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4b93-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="f4b93-103">Você usa uma instrução de atribuição normal para atribuir um objeto a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="f4b93-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="f4b93-104">Você pode atribuir uma expressão de objeto ou a palavra-chave [Nothing](../../../language-reference/nothing.md) , como ilustra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4b93-104">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="f4b93-105">`Nothing`significa que não há nenhum objeto atribuído atualmente à variável.</span><span class="sxs-lookup"><span data-stu-id="f4b93-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="f4b93-106">Inicialização</span><span class="sxs-lookup"><span data-stu-id="f4b93-106">Initialization</span></span>

<span data-ttu-id="f4b93-107">Quando o código começar a ser executado, suas variáveis de objeto serão inicializadas para `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="f4b93-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="f4b93-108">Aquelas cujas declarações incluem inicialização são reinicializadas para os valores que você especifica quando as instruções de declaração são executadas.</span><span class="sxs-lookup"><span data-stu-id="f4b93-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="f4b93-109">Você pode incluir a inicialização em sua declaração usando a [nova](../../../language-reference/operators/new-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f4b93-109">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="f4b93-110">As instruções de declaração a seguir declaram variáveis `testUri` de objeto e `ver` atribuem objetos específicos a elas.</span><span class="sxs-lookup"><span data-stu-id="f4b93-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="f4b93-111">Cada um deles usa um dos construtores sobrecarregados da classe apropriada para inicializar o objeto.</span><span class="sxs-lookup"><span data-stu-id="f4b93-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="f4b93-112">Dissociação</span><span class="sxs-lookup"><span data-stu-id="f4b93-112">Disassociation</span></span>

<span data-ttu-id="f4b93-113">Definir uma variável de objeto para `Nothing` interromper a associação da variável com qualquer objeto específico.</span><span class="sxs-lookup"><span data-stu-id="f4b93-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="f4b93-114">Isso impede que você altere acidentalmente o objeto alterando a variável.</span><span class="sxs-lookup"><span data-stu-id="f4b93-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="f4b93-115">Ele também permite que você teste se a variável de objeto aponta para um objeto válido, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4b93-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="f4b93-116">Se o objeto ao qual sua variável se refere estiver em outro aplicativo, esse teste não poderá determinar se o aplicativo foi encerrado ou simplesmente invalidará o objeto.</span><span class="sxs-lookup"><span data-stu-id="f4b93-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="f4b93-117">Uma variável de objeto com um valor de `Nothing` também é chamada de *referência nula*.</span><span class="sxs-lookup"><span data-stu-id="f4b93-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="f4b93-118">Instância atual</span><span class="sxs-lookup"><span data-stu-id="f4b93-118">Current Instance</span></span>

<span data-ttu-id="f4b93-119">A *instância atual* de um objeto é aquela em que o código está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="f4b93-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="f4b93-120">Como todo o código é executado dentro de um procedimento, a instância atual é aquela em que o procedimento foi invocado.</span><span class="sxs-lookup"><span data-stu-id="f4b93-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="f4b93-121">A `Me` palavra-chave age como uma variável de objeto que faz referência à instância atual.</span><span class="sxs-lookup"><span data-stu-id="f4b93-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="f4b93-122">Se um procedimento não for [compartilhado](../../../language-reference/modifiers/shared.md), ele poderá usar a `Me` palavra-chave para obter um ponteiro para a instância atual.</span><span class="sxs-lookup"><span data-stu-id="f4b93-122">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="f4b93-123">Procedimentos compartilhados não podem ser associados a uma instância específica de uma classe.</span><span class="sxs-lookup"><span data-stu-id="f4b93-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="f4b93-124">O uso do `Me` é particularmente útil para passar a instância atual para um procedimento em outro módulo.</span><span class="sxs-lookup"><span data-stu-id="f4b93-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="f4b93-125">Por exemplo, suponha que você tenha um número de documentos XML e queira adicionar texto padrão a todos eles.</span><span class="sxs-lookup"><span data-stu-id="f4b93-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="f4b93-126">O exemplo a seguir define um procedimento para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f4b93-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="f4b93-127">Cada objeto de documento XML poderia então chamar o procedimento e passar sua instância atual como um argumento.</span><span class="sxs-lookup"><span data-stu-id="f4b93-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="f4b93-128">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="f4b93-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="f4b93-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4b93-129">See also</span></span>

- [<span data-ttu-id="f4b93-130">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="f4b93-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="f4b93-131">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="f4b93-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="f4b93-132">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="f4b93-132">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="f4b93-133">Como declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4b93-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="f4b93-134">Como fazer uma variável de objeto não se referir a nenhuma instância</span><span class="sxs-lookup"><span data-stu-id="f4b93-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="f4b93-135">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="f4b93-135">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
