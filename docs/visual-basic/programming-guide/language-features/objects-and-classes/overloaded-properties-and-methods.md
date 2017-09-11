---
title: "Sobrecarregado propriedades e métodos (Visual Basic) | Documentos do Microsoft"
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
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
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
ms.openlocfilehash: 0b0040f78fd8e091027e32efae3a0f26c2a08622
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="1ea86-102">Propriedades e métodos sobrecarregados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ea86-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="1ea86-103">Sobrecarga é a criação de mais de um procedimento, construtor de instância ou propriedade em uma classe com o mesmo nome mas com tipos diferentes de argumentos.</span><span class="sxs-lookup"><span data-stu-id="1ea86-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="1ea86-104">Sobrecarga de uso</span><span class="sxs-lookup"><span data-stu-id="1ea86-104">Overloading Usage</span></span>  
 <span data-ttu-id="1ea86-105">Sobrecarga é especialmente útil quando o modelo de objeto determina que utilizam nomes idênticos para procedimentos que operam em diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="1ea86-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="1ea86-106">Por exemplo, uma classe que pode exibir vários tipos diferentes de dados poderia ter `Display` procedimentos que esta aparência:</span><span class="sxs-lookup"><span data-stu-id="1ea86-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 <span data-ttu-id="1ea86-107">[!code-vb[VbVbalrOOP&#64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ea86-107">[!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="1ea86-108">Sem sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="1ea86-108">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 <span data-ttu-id="1ea86-109">[!code-vb[VbVbalrOOP&#65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ea86-109">[!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="1ea86-110">Sobrecarga torna mais fácil de usar propriedades ou métodos porque ele fornece uma variedade de tipos de dados que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="1ea86-110">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="1ea86-111">Por exemplo, sobrecarregados `Display` método discutido anteriormente pode ser chamado com qualquer uma das seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="1ea86-111">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 <span data-ttu-id="1ea86-112">[!code-vb[VbVbalrOOP&#66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ea86-112">[!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="1ea86-113">Em tempo de execução [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o procedimento correto com base nos tipos de dados dos parâmetros você especifica.</span><span class="sxs-lookup"><span data-stu-id="1ea86-113">At run time, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="1ea86-114">Sobrecarga de regras</span><span class="sxs-lookup"><span data-stu-id="1ea86-114">Overloading Rules</span></span>  
 <span data-ttu-id="1ea86-115">Você pode criar um membro sobrecarregadas para uma classe adicionando dois ou mais propriedades ou métodos com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="1ea86-115">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="1ea86-116">Exceto para membros derivados sobrecarregados, cada membro sobrecarregadas deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferencial ao sobrecarregar uma propriedade ou um procedimento:</span><span class="sxs-lookup"><span data-stu-id="1ea86-116">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="1ea86-117">Modificadores, como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.</span><span class="sxs-lookup"><span data-stu-id="1ea86-117">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="1ea86-118">Nomes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ea86-118">Names of parameters</span></span>  
  
-   <span data-ttu-id="1ea86-119">Tipos de procedimentos de retorno</span><span class="sxs-lookup"><span data-stu-id="1ea86-119">Return types of procedures</span></span>  
  
 <span data-ttu-id="1ea86-120">O `Overloads` palavra-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa o `Overloads` palavra-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="1ea86-120">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="1ea86-121">Classes derivadas podem sobrecarregar membros herdados que possuem membros que têm parâmetros idênticos e tipos de parâmetro, um processo conhecido como *sombreamento por nome e assinatura*.</span><span class="sxs-lookup"><span data-stu-id="1ea86-121">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="1ea86-122">Se o `Overloads` palavra-chave é usada quando o sombreamento por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação na classe base e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="1ea86-122">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="1ea86-123">Se o `Overloads` palavra-chave for omitida quando um membro herdado com um membro que tem parâmetros idênticos e tipos de parâmetro de sobrecarga e a sobrecarga é chamada *sombreamento por nome*.</span><span class="sxs-lookup"><span data-stu-id="1ea86-123">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="1ea86-124">Sombreamento pelo nome substitui a implementação herdada de um membro, e torna todas as outras sobrecargas indisponível para instâncias da classe derivada e suas decedents.</span><span class="sxs-lookup"><span data-stu-id="1ea86-124">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="1ea86-125">O `Overloads` e `Shadows` modificadores não podem ser usados com a mesma propriedade ou método.</span><span class="sxs-lookup"><span data-stu-id="1ea86-125">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="1ea86-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ea86-126">Example</span></span>  
 <span data-ttu-id="1ea86-127">O exemplo a seguir cria os métodos sobrecarregados que aceitam um uma `String` ou `Decimal` representação de um valor em dólares e retornar uma cadeia de caracteres que contém o imposto sobre vendas.</span><span class="sxs-lookup"><span data-stu-id="1ea86-127">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="1ea86-128">Para usar esse exemplo para criar um método sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="1ea86-128">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="1ea86-129">Abra um novo projeto e adicionar uma classe denominada `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="1ea86-129">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="1ea86-130">Adicione o seguinte código para o `TaxClass` classe.</span><span class="sxs-lookup"><span data-stu-id="1ea86-130">Add the following code to the `TaxClass` class.</span></span>  
  
     <span data-ttu-id="1ea86-131">[!code-vb[VbVbalrOOP&#67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ea86-131">[!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]</span></span>  
  
3.  <span data-ttu-id="1ea86-132">Adicione o seguinte procedimento para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="1ea86-132">Add the following procedure to your form.</span></span>  
  
     <span data-ttu-id="1ea86-133">[!code-vb[VbVbalrOOP&#68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ea86-133">[!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]</span></span>  
  
4.  <span data-ttu-id="1ea86-134">Adicionar um botão para o formulário e chamar o `ShowTax` procedimento o `Button1_Click` evento do botão.</span><span class="sxs-lookup"><span data-stu-id="1ea86-134">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="1ea86-135">Execute o projeto e clique no botão no formulário para testar a sobrecarga `ShowTax` procedimento.</span><span class="sxs-lookup"><span data-stu-id="1ea86-135">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="1ea86-136">Em tempo de execução, o compilador escolhe a função sobrecarregada apropriada que corresponde aos parâmetros que está sendo usados.</span><span class="sxs-lookup"><span data-stu-id="1ea86-136">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="1ea86-137">Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro é uma cadeia de caracteres e a mensagem "o preço é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1ea86-137">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="1ea86-138">Imposto é $5,12" é exibida.</span><span class="sxs-lookup"><span data-stu-id="1ea86-138">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="1ea86-139">`TaxAmount`é chamado com um `Decimal` valor na segunda vez e a mensagem, "preço é um Decimal.</span><span class="sxs-lookup"><span data-stu-id="1ea86-139">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="1ea86-140">Imposto é $5,12" é exibida.</span><span class="sxs-lookup"><span data-stu-id="1ea86-140">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea86-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ea86-141">See Also</span></span>  
 <span data-ttu-id="1ea86-142">[Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-142">[Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="1ea86-143"> [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-143"> [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span></span>  
<span data-ttu-id="1ea86-144"> [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-144"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="1ea86-145"> [Noções básicas sobre herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-145"> [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="1ea86-146"> [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-146"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="1ea86-147"> [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-147"> [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) </span></span>  
<span data-ttu-id="1ea86-148"> [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-148"> [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) </span></span>  
<span data-ttu-id="1ea86-149"> [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="1ea86-149"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="1ea86-150"> [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)</span><span class="sxs-lookup"><span data-stu-id="1ea86-150"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)</span></span>
