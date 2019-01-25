---
title: Propriedades e métodos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 472cd0dbfc0544477d8e368b553a454b977d633c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498603"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="d09c6-102">Propriedades e métodos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d09c6-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="d09c6-103">Sobrecarga é a criação de mais de um procedimento, o construtor de instância ou a propriedade em uma classe com o mesmo nome mas com tipos diferentes de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d09c6-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="d09c6-104">Sobrecarga de uso</span><span class="sxs-lookup"><span data-stu-id="d09c6-104">Overloading usage</span></span>

 <span data-ttu-id="d09c6-105">Sobrecarga é especialmente útil quando seu modelo de objeto dita utilizar nomes idênticos para os procedimentos que operam em tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="d09c6-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="d09c6-106">Por exemplo, uma classe que pode exibir vários tipos diferentes de dados poderia ter `Display` procedimentos ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="d09c6-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 <span data-ttu-id="d09c6-107">Sem a sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="d09c6-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 <span data-ttu-id="d09c6-108">Sobrecarregando torna mais fácil de usar propriedades ou métodos porque ele fornece uma variedade de tipos de dados que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="d09c6-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="d09c6-109">Por exemplo, sobrecarregado `Display` método discutido anteriormente pode ser chamado com qualquer uma das seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="d09c6-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 <span data-ttu-id="d09c6-110">Em tempo de execução, o Visual Basic chama o procedimento correto com base nos tipos de dados dos parâmetros que você especificar.</span><span class="sxs-lookup"><span data-stu-id="d09c6-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="d09c6-111">Sobrecarga de regras</span><span class="sxs-lookup"><span data-stu-id="d09c6-111">Overloading rules</span></span>

 <span data-ttu-id="d09c6-112">Você pode criar um membro sobrecarregado para uma classe com a adição de dois ou mais propriedades ou métodos com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="d09c6-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="d09c6-113">Exceto para membros derivados sobrecarregados, cada membro sobrecarregado deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferenciador ao sobrecarregar uma propriedade ou procedimento:</span><span class="sxs-lookup"><span data-stu-id="d09c6-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="d09c6-114">Modificadores, tais como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.</span><span class="sxs-lookup"><span data-stu-id="d09c6-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="d09c6-115">Nomes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="d09c6-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="d09c6-116">Tipos de retorno de procedimentos</span><span class="sxs-lookup"><span data-stu-id="d09c6-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="d09c6-117">O `Overloads` palavra-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa o `Overloads` palavra-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d09c6-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="d09c6-118">As classes derivadas podem sobrecarregar membros herdados com membros que têm parâmetros idênticos e tipos de parâmetro, um processo conhecido como *sombreamento por nome e assinatura*.</span><span class="sxs-lookup"><span data-stu-id="d09c6-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="d09c6-119">Se o `Overloads` palavra-chave é usada quando o sombreamento por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação na classe base e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias das classe derivada.</span><span class="sxs-lookup"><span data-stu-id="d09c6-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="d09c6-120">Se o `Overloads` palavra-chave for omitida, ao sobrecarregar um membro herdado com um membro que tem parâmetros idênticos e tipos de parâmetro e, em seguida, a sobrecarga é chamado *sombreamento por nome*.</span><span class="sxs-lookup"><span data-stu-id="d09c6-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="d09c6-121">Sombreamento por nome substitui a implementação herdada de um membro e, em seguida, faz todas as outras sobrecargas indisponível para instâncias da classe derivada e seus decedents.</span><span class="sxs-lookup"><span data-stu-id="d09c6-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="d09c6-122">O `Overloads` e `Shadows` modificadores não podem ambos ser usados com a mesma propriedade ou método.</span><span class="sxs-lookup"><span data-stu-id="d09c6-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d09c6-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d09c6-123">Example</span></span>

 <span data-ttu-id="d09c6-124">O exemplo a seguir cria métodos sobrecarregados que aceitam a um `String` ou `Decimal` representação de um valor monetário e o retorno de uma cadeia de caracteres que contém o imposto sobre vendas.</span><span class="sxs-lookup"><span data-stu-id="d09c6-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="d09c6-125">Para usar este exemplo para criar um método sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="d09c6-125">To use this example to create an overloaded method</span></span>
  
1.  <span data-ttu-id="d09c6-126">Abra um novo projeto e adicione uma classe chamada `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="d09c6-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="d09c6-127">Adicione o código a seguir à classe `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="d09c6-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  <span data-ttu-id="d09c6-128">Adicione o procedimento a seguir ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d09c6-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  <span data-ttu-id="d09c6-129">Adicionar um botão ao formulário e chame o `ShowTax` procedimento do `Button1_Click` evento do botão.</span><span class="sxs-lookup"><span data-stu-id="d09c6-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="d09c6-130">Execute o projeto e clique no botão no formulário para testar sobrecarregado `ShowTax` procedimento.</span><span class="sxs-lookup"><span data-stu-id="d09c6-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="d09c6-131">Em tempo de execução, o compilador escolhe a função sobrecarregada apropriada que corresponde aos parâmetros que está sendo usados.</span><span class="sxs-lookup"><span data-stu-id="d09c6-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="d09c6-132">Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro que é uma cadeia de caracteres e a mensagem "o preço é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d09c6-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="d09c6-133">Imposto é $5,12" é exibida.</span><span class="sxs-lookup"><span data-stu-id="d09c6-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="d09c6-134">`TaxAmount` é chamado com um `Decimal` valor na segunda vez e a mensagem, "preço é um Decimal.</span><span class="sxs-lookup"><span data-stu-id="d09c6-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="d09c6-135">Imposto é $5,12" é exibida.</span><span class="sxs-lookup"><span data-stu-id="d09c6-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09c6-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d09c6-136">See also</span></span>

- [<span data-ttu-id="d09c6-137">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="d09c6-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="d09c6-138">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d09c6-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="d09c6-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d09c6-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d09c6-140">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="d09c6-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="d09c6-141">Sombras</span><span class="sxs-lookup"><span data-stu-id="d09c6-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="d09c6-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="d09c6-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="d09c6-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="d09c6-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="d09c6-144">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="d09c6-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="d09c6-145">Sombras</span><span class="sxs-lookup"><span data-stu-id="d09c6-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
