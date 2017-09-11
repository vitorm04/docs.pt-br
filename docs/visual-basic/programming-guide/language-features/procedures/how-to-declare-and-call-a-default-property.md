---
title: "Como: declarar e chamar uma propriedade padrão no Visual Basic | Documentos do Microsoft"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: 7cfd476def67ccf46e524da7943680f9e34b6a26
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="732d6-102">Como declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="732d6-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="732d6-103">A *propriedade padrão* é uma propriedade de classe ou estrutura que seu código pode acessar sem especificá-la.</span><span class="sxs-lookup"><span data-stu-id="732d6-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="732d6-104">Ao chamar por apelidos uma classe ou estrutura, mas não uma propriedade e o contexto permite o acesso a uma propriedade [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] decide o acesso à propriedade dessa classe ou da estrutura padrão, se houver.</span><span class="sxs-lookup"><span data-stu-id="732d6-104">When calling code names a class or structure but not a property, and the context allows access to a property, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="732d6-105">Uma classe ou estrutura pode ter no máximo uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="732d6-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="732d6-106">No entanto, você pode sobrecarregar uma propriedade padrão e ter mais de uma versão dele.</span><span class="sxs-lookup"><span data-stu-id="732d6-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="732d6-107">Para obter mais informações, consulte [padrão](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="732d6-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="732d6-108">Para declarar uma propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="732d6-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="732d6-109">Declare a propriedade da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="732d6-109">Declare the property in the normal way.</span></span> <span data-ttu-id="732d6-110">Não especifique o `Shared` ou `Private` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="732d6-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="732d6-111">Incluir o `Default` palavra-chave na declaração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="732d6-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="732d6-112">Especifique pelo menos um parâmetro para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="732d6-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="732d6-113">Você não pode definir uma propriedade padrão que têm pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="732d6-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     <span data-ttu-id="732d6-114">[!code-vb[17 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-114">[!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span></span>  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="732d6-115">Para chamar uma propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="732d6-115">To call a default property</span></span>  
  
1.  <span data-ttu-id="732d6-116">Declare uma variável do tipo de classe ou estrutura que contém.</span><span class="sxs-lookup"><span data-stu-id="732d6-116">Declare a variable of the containing class or structure type.</span></span>  
  
     <span data-ttu-id="732d6-117">[!code-vb[VbVbcnProcedures n º&16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-117">[!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span></span>  
  
2.  <span data-ttu-id="732d6-118">Use o nome de variável sozinho em uma expressão em que você normalmente incluiria o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="732d6-118">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     <span data-ttu-id="732d6-119">[!code-vb[VbVbcnProcedures&#21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-119">[!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span></span>  
  
3.  <span data-ttu-id="732d6-120">Siga o nome da variável com uma lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="732d6-120">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="732d6-121">Uma propriedade padrão deve receber pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="732d6-121">A default property must take at least one argument.</span></span>  
  
     <span data-ttu-id="732d6-122">[!code-vb[20 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-122">[!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span></span>  
  
4.  <span data-ttu-id="732d6-123">Para recuperar o valor da propriedade padrão, use o nome da variável com uma lista de argumentos, em uma expressão ou depois de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="732d6-123">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="732d6-124">[!code-vb[VbVbcnProcedures&#15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-124">[!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span></span>  
  
5.  <span data-ttu-id="732d6-125">Para definir o valor da propriedade padrão, use o nome da variável com uma lista de argumentos, no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="732d6-125">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="732d6-126">[!code-vb[VbVbcnProcedures&#14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-126">[!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span></span>  
  
6.  <span data-ttu-id="732d6-127">Você sempre pode especificar o nome da propriedade padrão junto com o nome da variável, exatamente como você faria para acessar qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="732d6-127">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     <span data-ttu-id="732d6-128">[!code-vb[19 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-128">[!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="732d6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="732d6-129">Example</span></span>  
 <span data-ttu-id="732d6-130">O exemplo a seguir declara uma propriedade padrão em uma classe.</span><span class="sxs-lookup"><span data-stu-id="732d6-130">The following example declares a default property on a class.</span></span>  
  
 <span data-ttu-id="732d6-131">[!code-vb[VbVbcnProcedures&#12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-131">[!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="732d6-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="732d6-132">Example</span></span>  
 <span data-ttu-id="732d6-133">O exemplo a seguir demonstra como chamar a propriedade padrão `myProperty` na classe `class1`.</span><span class="sxs-lookup"><span data-stu-id="732d6-133">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="732d6-134">As três declarações de atribuição armazenam valores em `myProperty`e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>chamada lê os valores.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="732d6-134">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 <span data-ttu-id="732d6-135">[!code-vb[VbVbcnProcedures&13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="732d6-135">[!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span></span>  
  
 <span data-ttu-id="732d6-136">O uso mais comum de uma propriedade padrão é o <xref:Microsoft.VisualBasic.Collection.Item%2A>propriedade em várias classes de coleção.</xref:Microsoft.VisualBasic.Collection.Item%2A></span><span class="sxs-lookup"><span data-stu-id="732d6-136">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="732d6-137">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="732d6-137">Robust Programming</span></span>  
 <span data-ttu-id="732d6-138">Propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="732d6-138">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="732d6-139">Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="732d6-139">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="732d6-140">Isso pode levar a erros de compilador ou lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="732d6-140">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="732d6-141">Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo do compilador para `On`.</span><span class="sxs-lookup"><span data-stu-id="732d6-141">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="732d6-142">Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ele tem uma propriedade padrão e, nesse caso, o que seu nome é.</span><span class="sxs-lookup"><span data-stu-id="732d6-142">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="732d6-143">Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="732d6-143">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="732d6-144">Para fins de legibilidade de código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="732d6-144">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="732d6-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="732d6-145">See Also</span></span>  
 <span data-ttu-id="732d6-146">[Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-146">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="732d6-147"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-147"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="732d6-148"> [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-148"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="732d6-149"> [Padrão](../../../../visual-basic/language-reference/modifiers/default.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-149"> [Default](../../../../visual-basic/language-reference/modifiers/default.md) </span></span>  
<span data-ttu-id="732d6-150"> [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-150"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="732d6-151"> [Como: criar uma propriedade](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-151"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="732d6-152"> [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-152"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="732d6-153"> [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-153"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="732d6-154"> [Como: inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="732d6-154"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="732d6-155">Como obter um valor de uma propriedade (Visual Basic) [Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="732d6-155"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
