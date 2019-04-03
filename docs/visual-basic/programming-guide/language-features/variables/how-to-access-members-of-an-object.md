---
title: 'Como: Acessar membros de um objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2b7e600a23ed326fe3e914957b4e698bc34c6135
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819639"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="9e8de-102">Como: Acessar membros de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e8de-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="9e8de-103">Quando você tiver uma variável de objeto que se refere a um objeto, você geralmente deseja trabalhar com os membros desse objeto, como seus métodos, propriedades, campos e eventos.</span><span class="sxs-lookup"><span data-stu-id="9e8de-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="9e8de-104">Por exemplo, depois de criar um novo <xref:System.Windows.Forms.Form> do objeto, você poderá definir seus <xref:System.Windows.Forms.Control.Text%2A> propriedade ou chamada seu <xref:System.Windows.Forms.Control.Focus%2A> método.</span><span class="sxs-lookup"><span data-stu-id="9e8de-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="9e8de-105">Acessando membros</span><span class="sxs-lookup"><span data-stu-id="9e8de-105">Accessing Members</span></span>  
 <span data-ttu-id="9e8de-106">Você pode acessar membros de um objeto por meio da variável que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="9e8de-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="9e8de-107">Para acessar membros de um objeto</span><span class="sxs-lookup"><span data-stu-id="9e8de-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="9e8de-108">Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="9e8de-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="9e8de-109">Se o membro for [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), você não precisa de uma variável para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="9e8de-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="9e8de-110">Acessando membros de um objeto do tipo conhecido</span><span class="sxs-lookup"><span data-stu-id="9e8de-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="9e8de-111">Se você souber o tipo de um objeto em tempo de compilação, você pode usar *vinculação inicial* para uma variável que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="9e8de-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="9e8de-112">Para acessar membros de um objeto para o qual você sabe o tipo em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="9e8de-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="9e8de-113">Declare a variável de objeto para ser do tipo do objeto que você pretende atribuir à variável.</span><span class="sxs-lookup"><span data-stu-id="9e8de-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="9e8de-114">Com o `Option Strict On`, você pode atribuir apenas <xref:System.Windows.Forms.Form> objetos (ou objetos de um tipo derivam de <xref:System.Windows.Forms.Form>) para `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="9e8de-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="9e8de-115">Se você definiu uma classe ou estrutura com uma ampliação `CType` conversão <xref:System.Windows.Forms.Form>, você também pode atribuir essa classe ou estrutura para `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="9e8de-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="9e8de-116">Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="9e8de-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="9e8de-117">Você pode acessar todos os métodos e propriedades específicas para o <xref:System.Windows.Forms.Form> classe, não importa o que o `Option Strict` é de configuração.</span><span class="sxs-lookup"><span data-stu-id="9e8de-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="9e8de-118">Acessando membros de um objeto de tipo desconhecido</span><span class="sxs-lookup"><span data-stu-id="9e8de-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="9e8de-119">Se você não souber o tipo de um objeto em tempo de compilação, você deve usar *ligação tardia* para qualquer variável que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="9e8de-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="9e8de-120">Para acessar membros de um objeto para o qual você não souber o tipo em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="9e8de-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="9e8de-121">Declarar a variável de objeto para ser o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9e8de-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="9e8de-122">(Declarando uma variável como `Object` é o mesmo que declarar como <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="9e8de-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="9e8de-123">Com o `Option Strict On`, você pode acessar somente os membros que são definidos na <xref:System.Object> classe.</span><span class="sxs-lookup"><span data-stu-id="9e8de-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="9e8de-124">Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="9e8de-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="9e8de-125">Para poder acessar os membros de qualquer objeto que você atribui à variável de objeto, você deve definir `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="9e8de-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="9e8de-126">Quando você fizer isso, o compilador não pode garantir que um determinado membro é exposto pelo objeto que você atribui à variável.</span><span class="sxs-lookup"><span data-stu-id="9e8de-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="9e8de-127">Se o objeto não expõe um membro que você tentar acessar, um <xref:System.MemberAccessException> ocorrerá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9e8de-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e8de-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e8de-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="9e8de-129">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="9e8de-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="9e8de-130">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="9e8de-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="9e8de-131">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="9e8de-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="9e8de-132">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="9e8de-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
