---
title: Propriedades e métodos sobrecarregados
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 1672f12773ece012c580253b6dafbf9d0ac8f07c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389146"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="4da10-102">Propriedades e métodos sobrecarregados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4da10-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="4da10-103">O sobrecarregamento é a criação de mais de um procedimento, Construtor de instância ou propriedade em uma classe com o mesmo nome, mas tipos de argumento diferentes.</span><span class="sxs-lookup"><span data-stu-id="4da10-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="4da10-104">Sobrecarregando o uso</span><span class="sxs-lookup"><span data-stu-id="4da10-104">Overloading usage</span></span>

<span data-ttu-id="4da10-105">O sobrecarregamento é especialmente útil quando o modelo de objeto determina que você emprega nomes idênticos para procedimentos que operam em diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="4da10-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="4da10-106">Por exemplo, uma classe que pode exibir vários tipos de dados diferentes pode ter `Display` procedimentos parecidos com estes:</span><span class="sxs-lookup"><span data-stu-id="4da10-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="4da10-107">Sem sobrecarga, você precisaria criar nomes distintos para cada procedimento, embora eles façam a mesma coisa, conforme mostrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="4da10-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="4da10-108">O sobrecarregamento facilita o uso de propriedades ou métodos, pois ele fornece uma opção de tipos de dados que podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="4da10-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="4da10-109">Por exemplo, o `Display` método sobrecarregado discutido anteriormente pode ser chamado com qualquer uma das seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="4da10-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="4da10-110">Em tempo de execução, Visual Basic chama o procedimento correto com base nos tipos de dados dos parâmetros que você especificar.</span><span class="sxs-lookup"><span data-stu-id="4da10-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="4da10-111">Regras de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="4da10-111">Overloading rules</span></span>

 <span data-ttu-id="4da10-112">Você cria um membro sobrecarregado para uma classe adicionando duas ou mais propriedades ou métodos com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4da10-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="4da10-113">Exceto para membros derivados sobrecarregados, cada membro sobrecarregado deve ter diferentes listas de parâmetros e os seguintes itens não podem ser usados como um recurso de diferenciação ao sobrecarregar uma propriedade ou um procedimento:</span><span class="sxs-lookup"><span data-stu-id="4da10-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="4da10-114">Modificadores, como `ByVal` ou `ByRef` , que se aplicam a um membro ou parâmetros do membro.</span><span class="sxs-lookup"><span data-stu-id="4da10-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="4da10-115">Nomes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="4da10-115">Names of parameters</span></span>

- <span data-ttu-id="4da10-116">Tipos de retorno de procedimentos</span><span class="sxs-lookup"><span data-stu-id="4da10-116">Return types of procedures</span></span>

<span data-ttu-id="4da10-117">A `Overloads` palavra-chave é opcional ao sobrecarregar, mas se qualquer membro sobrecarregado usar a `Overloads` palavra-chave, todos os outros Membros sobrecarregados com o mesmo nome também deverão especificar essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="4da10-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="4da10-118">Classes derivadas podem sobrecarregar membros herdados com membros que têm parâmetros e tipos de parâmetros idênticos, um processo conhecido como *sombreamento por nome e assinatura*.</span><span class="sxs-lookup"><span data-stu-id="4da10-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="4da10-119">Se a `Overloads` palavra-chave for usada ao sombrear por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação na classe base, e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="4da10-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="4da10-120">Se a `Overloads` palavra-chave for omitida ao sobrecarregar um membro herdado com um membro que tenha parâmetros e tipos de parâmetros idênticos, o sobrecarregamento será chamado de *sombreamento por nome*.</span><span class="sxs-lookup"><span data-stu-id="4da10-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="4da10-121">Sombrear por nome substitui a implementação herdada de um membro e faz com que todas as outras sobrecargas não estejam disponíveis para instâncias da classe derivada e seu decedents.</span><span class="sxs-lookup"><span data-stu-id="4da10-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="4da10-122">Os `Overloads` `Shadows` modificadores e não podem ser usados com a mesma propriedade ou método.</span><span class="sxs-lookup"><span data-stu-id="4da10-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="4da10-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4da10-123">Example</span></span>

<span data-ttu-id="4da10-124">O exemplo a seguir cria métodos sobrecarregados que aceitam `String` uma `Decimal` representação or de um valor de dólar e retornam uma cadeia de caracteres que contém o imposto sobre vendas.</span><span class="sxs-lookup"><span data-stu-id="4da10-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="4da10-125">Para usar este exemplo para criar um método sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="4da10-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="4da10-126">Abra um novo projeto e adicione uma classe chamada `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="4da10-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="4da10-127">Adicione o código a seguir à classe `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="4da10-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="4da10-128">Adicione o procedimento a seguir ao formulário.</span><span class="sxs-lookup"><span data-stu-id="4da10-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="4da10-129">Adicione um botão ao formulário e chame o `ShowTax` procedimento do `Button1_Click` evento do botão.</span><span class="sxs-lookup"><span data-stu-id="4da10-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="4da10-130">Execute o projeto e clique no botão no formulário para testar o `ShowTax` procedimento sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="4da10-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="4da10-131">Em tempo de execução, o compilador escolhe a função sobrecarregada apropriada que corresponde aos parâmetros que estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="4da10-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="4da10-132">Quando você clica no botão, o método sobrecarregado é chamado primeiro com um `Price` parâmetro que é uma cadeia de caracteres e a mensagem, "Price é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4da10-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="4da10-133">O imposto é $5.12 "é exibido.</span><span class="sxs-lookup"><span data-stu-id="4da10-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="4da10-134">`TaxAmount`é chamado com um `Decimal` valor da segunda vez e da mensagem, "Price é um decimal.</span><span class="sxs-lookup"><span data-stu-id="4da10-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="4da10-135">O imposto é $5.12 "é exibido.</span><span class="sxs-lookup"><span data-stu-id="4da10-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4da10-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="4da10-136">See also</span></span>

- [<span data-ttu-id="4da10-137">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="4da10-137">Objects and Classes</span></span>](index.md)
- [<span data-ttu-id="4da10-138">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4da10-138">Shadowing in Visual Basic</span></span>](../declared-elements/shadowing.md)
- [<span data-ttu-id="4da10-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="4da10-139">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4da10-140">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="4da10-140">Inheritance Basics</span></span>](inheritance-basics.md)
- [<span data-ttu-id="4da10-141">Sombras</span><span class="sxs-lookup"><span data-stu-id="4da10-141">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="4da10-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="4da10-142">ByVal</span></span>](../../../language-reference/modifiers/byval.md)
- [<span data-ttu-id="4da10-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="4da10-143">ByRef</span></span>](../../../language-reference/modifiers/byref.md)
- [<span data-ttu-id="4da10-144">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="4da10-144">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="4da10-145">Sombras</span><span class="sxs-lookup"><span data-stu-id="4da10-145">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
