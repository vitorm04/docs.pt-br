---
title: 'Como: Declarar e chamar uma propriedade padrão no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: ca282acbe6831f2189d83faa2f83d32d420d9b53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640960"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="e2eb9-102">Como: Declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2eb9-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="e2eb9-103">Um *propriedade padrão* é uma propriedade de classe ou estrutura que seu código pode acessar sem especificá-lo.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="e2eb9-104">Ao chamar código nomes de uma classe ou estrutura, mas não uma propriedade e o contexto permite o acesso a uma propriedade, Visual Basic decide o acesso à propriedade dessa classe ou da estrutura padrão, se houver.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="e2eb9-105">Uma classe ou estrutura pode ter no máximo uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="e2eb9-106">No entanto, você pode sobrecarregar uma propriedade padrão e ter mais de uma versão dele.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="e2eb9-107">Para obter mais informações, consulte [padrão](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="e2eb9-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="e2eb9-108">Para declarar uma propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="e2eb9-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="e2eb9-109">Declare a propriedade da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-109">Declare the property in the normal way.</span></span> <span data-ttu-id="e2eb9-110">Não especifique a `Shared` ou `Private` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="e2eb9-111">Incluir o `Default` palavra-chave na declaração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="e2eb9-112">Especifique pelo menos um parâmetro para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="e2eb9-113">Você não pode definir uma propriedade padrão que têm pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="e2eb9-114">Para chamar uma propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="e2eb9-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="e2eb9-115">Declare uma variável do tipo recipiente de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  <span data-ttu-id="e2eb9-116">Use o nome da variável sozinho em uma expressão em que você normalmente incluiria o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  <span data-ttu-id="e2eb9-117">Siga o nome da variável com uma lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="e2eb9-118">Uma propriedade de padrão deve ter pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  <span data-ttu-id="e2eb9-119">Para recuperar o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos, em uma expressão ou igual a seguir (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  <span data-ttu-id="e2eb9-120">Para definir o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  <span data-ttu-id="e2eb9-121">Você sempre pode especificar o nome da propriedade padrão junto com o nome da variável, exatamente como você faria para acessar qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="e2eb9-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2eb9-122">Example</span></span>  
 <span data-ttu-id="e2eb9-123">O exemplo a seguir declara uma propriedade padrão em uma classe.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a><span data-ttu-id="e2eb9-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2eb9-124">Example</span></span>  
 <span data-ttu-id="e2eb9-125">O exemplo a seguir demonstra como chamar a propriedade padrão `myProperty` na classe `class1`.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="e2eb9-126">As três declarações de atribuição armazenam valores em `myProperty`e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada lê os valores.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 <span data-ttu-id="e2eb9-127">O uso mais comum de uma propriedade padrão é o <xref:Microsoft.VisualBasic.Collection.Item%2A> propriedade em várias classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e2eb9-128">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e2eb9-128">Robust Programming</span></span>  
 <span data-ttu-id="e2eb9-129">As propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="e2eb9-130">Se o código de chamada não estiver familiarizado com a sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="e2eb9-131">Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="e2eb9-132">Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo de compilador verificando para `On`.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="e2eb9-133">Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ele tem uma propriedade padrão e nesse caso, o que seu nome é.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="e2eb9-134">Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="e2eb9-135">Para facilitar a leitura do código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="e2eb9-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2eb9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2eb9-136">See also</span></span>
- [<span data-ttu-id="e2eb9-137">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="e2eb9-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e2eb9-138">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="e2eb9-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e2eb9-139">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="e2eb9-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e2eb9-140">Padrão</span><span class="sxs-lookup"><span data-stu-id="e2eb9-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)
- [<span data-ttu-id="e2eb9-141">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2eb9-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="e2eb9-142">Como: Criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="e2eb9-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="e2eb9-143">Como: Declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="e2eb9-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="e2eb9-144">Como: Chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="e2eb9-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="e2eb9-145">Como: Inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="e2eb9-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="e2eb9-146">Como: Obter um valor de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="e2eb9-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
