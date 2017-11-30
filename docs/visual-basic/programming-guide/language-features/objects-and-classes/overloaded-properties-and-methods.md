---
title: "Propriedades e métodos sobrecarregados (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a872540716941ccd0dbb8b058508b89ce26a988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="f12f2-102">Propriedades e métodos sobrecarregados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f12f2-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="f12f2-103">Sobrecarga é a criação de mais de um procedimento, construtor de instância ou propriedade em uma classe com o mesmo nome mas com tipos diferentes de argumentos.</span><span class="sxs-lookup"><span data-stu-id="f12f2-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="f12f2-104">Sobrecarga de uso</span><span class="sxs-lookup"><span data-stu-id="f12f2-104">Overloading Usage</span></span>  
 <span data-ttu-id="f12f2-105">Sobrecarga é especialmente útil quando o modelo de objeto dita utilizar nomes idênticos de procedimentos que operam em diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="f12f2-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="f12f2-106">Por exemplo, uma classe que pode exibir vários tipos de dados diferentes pode ter `Display` procedimentos ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="f12f2-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 <span data-ttu-id="f12f2-107">Sem sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="f12f2-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 <span data-ttu-id="f12f2-108">Sobrecarga torna mais fácil de usar propriedades ou métodos porque ele fornece uma variedade de tipos de dados que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="f12f2-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="f12f2-109">Por exemplo, o sobrecarregado `Display` método discutido anteriormente pode ser chamado com qualquer uma das linhas de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f12f2-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 <span data-ttu-id="f12f2-110">Em tempo de execução [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chama o procedimento correto com base nos tipos de dados dos parâmetros você especifica.</span><span class="sxs-lookup"><span data-stu-id="f12f2-110">At run time, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="f12f2-111">Sobrecarga de regras</span><span class="sxs-lookup"><span data-stu-id="f12f2-111">Overloading Rules</span></span>  
 <span data-ttu-id="f12f2-112">Você pode criar um membro sobrecarregado para uma classe adicionando dois ou mais propriedades ou métodos com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="f12f2-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="f12f2-113">Exceto para membros derivados sobrecarregados, cada membro sobrecarregado deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferencial ao sobrecarregar uma propriedade ou procedimento:</span><span class="sxs-lookup"><span data-stu-id="f12f2-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="f12f2-114">Modificadores, tais como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.</span><span class="sxs-lookup"><span data-stu-id="f12f2-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="f12f2-115">Nomes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="f12f2-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="f12f2-116">Tipos de retorno de procedimentos</span><span class="sxs-lookup"><span data-stu-id="f12f2-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="f12f2-117">O `Overloads` palavra-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa o `Overloads` palavra-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f12f2-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="f12f2-118">Classes derivadas podem sobrecarregar membros herdados com membros que têm parâmetros idênticos e tipos de parâmetro, um processo conhecido como *sombreamento por nome e assinatura*.</span><span class="sxs-lookup"><span data-stu-id="f12f2-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="f12f2-119">Se o `Overloads` palavra-chave é usada quando sombreamento por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação da classe base e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias das classe derivada.</span><span class="sxs-lookup"><span data-stu-id="f12f2-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="f12f2-120">Se o `Overloads` palavra-chave for omitida ao sobrecarregar um membro herdado com um membro que tem parâmetros idênticos e tipos de parâmetro e, em seguida, a sobrecarga é chamado *sombreamento por nome*.</span><span class="sxs-lookup"><span data-stu-id="f12f2-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="f12f2-121">Sombreamento pelo nome substitui a implementação herdada de um membro e torna todas as outras sobrecargas disponíveis para instâncias de classe derivada e seus decedents.</span><span class="sxs-lookup"><span data-stu-id="f12f2-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="f12f2-122">O `Overloads` e `Shadows` modificadores não podem ser usados com o mesmo método ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="f12f2-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f12f2-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f12f2-123">Example</span></span>  
 <span data-ttu-id="f12f2-124">O exemplo a seguir cria os métodos sobrecarregados que aceitam um um `String` ou `Decimal` representação de um valor monetário e retornar uma cadeia de caracteres que contém o imposto sobre vendas.</span><span class="sxs-lookup"><span data-stu-id="f12f2-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="f12f2-125">Para usar este exemplo para criar um método sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="f12f2-125">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="f12f2-126">Abra um novo projeto e adicione uma classe denominada `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="f12f2-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="f12f2-127">Adicione o seguinte código para o `TaxClass` classe.</span><span class="sxs-lookup"><span data-stu-id="f12f2-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  <span data-ttu-id="f12f2-128">Adicione o seguinte procedimento para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="f12f2-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  <span data-ttu-id="f12f2-129">Adicionar um botão ao seu formulário e a chamada a `ShowTax` procedimento o `Button1_Click` eventos do botão.</span><span class="sxs-lookup"><span data-stu-id="f12f2-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="f12f2-130">Execute o projeto e clique no botão no formulário para testar o sobrecarregado `ShowTax` procedimento.</span><span class="sxs-lookup"><span data-stu-id="f12f2-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="f12f2-131">Em tempo de execução, o compilador escolha a função sobrecarregada apropriada que corresponde aos parâmetros que está sendo usados.</span><span class="sxs-lookup"><span data-stu-id="f12f2-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="f12f2-132">Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro que é uma cadeia de caracteres e a mensagem "o preço é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f12f2-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="f12f2-133">Imposto é $5,12" é exibida.</span><span class="sxs-lookup"><span data-stu-id="f12f2-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="f12f2-134">`TaxAmount`é chamado com um `Decimal` valor na segunda vez e a mensagem, "o preço é um número Decimal.</span><span class="sxs-lookup"><span data-stu-id="f12f2-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="f12f2-135">Imposto é $5,12" é exibida.</span><span class="sxs-lookup"><span data-stu-id="f12f2-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12f2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f12f2-136">See Also</span></span>  
 [<span data-ttu-id="f12f2-137">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="f12f2-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="f12f2-138">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f12f2-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="f12f2-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="f12f2-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="f12f2-140">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="f12f2-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="f12f2-141">Sombras</span><span class="sxs-lookup"><span data-stu-id="f12f2-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="f12f2-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="f12f2-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [<span data-ttu-id="f12f2-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="f12f2-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [<span data-ttu-id="f12f2-144">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="f12f2-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="f12f2-145">Sombras</span><span class="sxs-lookup"><span data-stu-id="f12f2-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
