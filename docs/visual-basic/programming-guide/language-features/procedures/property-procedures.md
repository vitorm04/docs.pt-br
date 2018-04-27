---
title: Procedimentos de propriedade (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9df6f381c89263aa16315fb06a2b3b0d645bbf
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="9f615-102">Procedimentos de propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f615-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="9f615-103">Um procedimento de propriedade é uma série de instruções do Visual Basic que manipulam uma propriedade personalizada em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="9f615-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="9f615-104">Procedimentos de propriedade são também conhecidos como *acessadores de propriedade*.</span><span class="sxs-lookup"><span data-stu-id="9f615-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="9f615-105">Visual Basic fornece para os procedimentos de propriedade a seguir:</span><span class="sxs-lookup"><span data-stu-id="9f615-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="9f615-106">Um `Get` procedimento retorna o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="9f615-107">Ele é chamado quando você acessa a propriedade em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="9f615-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="9f615-108">Um `Set` procedimento define uma propriedade com um valor, incluindo uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="9f615-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="9f615-109">Ele é chamado quando você atribui um valor à propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="9f615-110">Você geralmente define procedimentos de propriedade em pares, usando o `Get` e `Set` instruções, mas você pode definir um procedimento sozinho se a propriedade é somente leitura ([obter instrução](../../../../visual-basic/language-reference/statements/get-statement.md)) ou somente gravação ([definido Instrução](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="9f615-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="9f615-111">Você pode omitir o `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9f615-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="9f615-112">Para obter mais informações, consulte [Propriedades autoimplementadas](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="9f615-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="9f615-113">Você pode definir propriedades em classes, estruturas e módulos.</span><span class="sxs-lookup"><span data-stu-id="9f615-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="9f615-114">As propriedades são `Public` por padrão, que significa que você pode chamá-los de qualquer lugar no seu aplicativo que possa acessar o recipiente da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="9f615-115">Para obter uma comparação entre propriedades e variáveis, consulte [diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="9f615-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="9f615-116">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="9f615-116">Declaration Syntax</span></span>  
 <span data-ttu-id="9f615-117">A propriedade em si é definida por um bloco de código entre as [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="9f615-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="9f615-118">Dentro deste bloco, cada procedimento de propriedade aparece como um bloco interno incluído dentro de uma instrução de declaração (`Get` ou `Set`) e a correspondência `End` declaração.</span><span class="sxs-lookup"><span data-stu-id="9f615-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="9f615-119">A sintaxe para declarar uma propriedade e seus procedimentos é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f615-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="9f615-120">O `Modifiers` pode especificar o nível de acesso e informações sobre a sobrecarga, substituindo, compartilhando e sombreamento, bem como se a propriedade é somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="9f615-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="9f615-121">O `AccessLevel` no `Get` ou `Set` procedimento pode ser qualquer nível que seja mais restritivo do que o nível de acesso especificado para a propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="9f615-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="9f615-122">Para obter mais informações, consulte [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9f615-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="9f615-123">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="9f615-123">Data Type</span></span>  
 <span data-ttu-id="9f615-124">Um tipo de dados e o nível de acesso principal são definidos no `Property` instrução, não nos procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="9f615-125">Uma propriedade pode ter apenas um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9f615-125">A property can have only one data type.</span></span> <span data-ttu-id="9f615-126">Por exemplo, você não pode definir uma propriedade para armazenar um `Decimal` valor mas recuperar um `Double` valor.</span><span class="sxs-lookup"><span data-stu-id="9f615-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="9f615-127">Nível de acesso</span><span class="sxs-lookup"><span data-stu-id="9f615-127">Access Level</span></span>  
 <span data-ttu-id="9f615-128">No entanto, você pode definir um nível de acesso principal para uma propriedade e restringir ainda mais o nível de acesso em um dos seus procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="9f615-129">Por exemplo, você pode definir um `Public` propriedade e, em seguida, definir uma `Private Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="9f615-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="9f615-130">O `Get` procedimento permanece `Public`.</span><span class="sxs-lookup"><span data-stu-id="9f615-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="9f615-131">Você pode alterar o nível de acesso em apenas um dos procedimentos de propriedade e só pode torná-lo mais restritivo do que o nível de acesso principal.</span><span class="sxs-lookup"><span data-stu-id="9f615-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="9f615-132">Para obter mais informações, consulte [como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9f615-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="9f615-133">Declaração de parâmetro</span><span class="sxs-lookup"><span data-stu-id="9f615-133">Parameter Declaration</span></span>  
 <span data-ttu-id="9f615-134">Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md), exceto que o mecanismo de passagem deve ser `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="9f615-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="9f615-135">A sintaxe para cada parâmetro na lista de parâmetros é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f615-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="9f615-136">Se o parâmetro é opcional, você também deve fornecer um valor padrão como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="9f615-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="9f615-137">A sintaxe para especificar um valor padrão é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f615-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="9f615-138">Valor de propriedade</span><span class="sxs-lookup"><span data-stu-id="9f615-138">Property Value</span></span>  
 <span data-ttu-id="9f615-139">Em um `Get` procedimento, o valor de retorno é fornecido para a expressão de chamada como o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="9f615-140">Em um `Set` procedimento, o novo valor da propriedade é passado para o parâmetro do `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="9f615-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="9f615-141">Se você declarar explicitamente um parâmetro, declare-o com o mesmo tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="9f615-142">Se você não declarar um parâmetro, o compilador usa o parâmetro implícito `Value` representar o novo valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="9f615-143">A sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="9f615-143">Calling Syntax</span></span>  
 <span data-ttu-id="9f615-144">Você chama um procedimento de propriedade implicitamente fazendo referência à propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f615-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="9f615-145">Use o nome da propriedade da mesma maneira que você usaria o nome de uma variável, exceto que você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="9f615-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="9f615-146">Se nenhum argumento for fornecido, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="9f615-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="9f615-147">A sintaxe para uma chamada implícita para um `Set` procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9f615-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="9f615-148">A sintaxe para uma chamada implícita para um `Get` procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9f615-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="9f615-149">Ilustração da declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="9f615-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="9f615-150">A propriedade a seguir armazena um nome completo como dois nomes constituintes, o nome e o sobrenome.</span><span class="sxs-lookup"><span data-stu-id="9f615-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="9f615-151">Quando o código de chamada lê `fullName`, o `Get` procedimento combina as duas partes e retorna o nome completo.</span><span class="sxs-lookup"><span data-stu-id="9f615-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="9f615-152">Quando o código de chamada atribui um novo nome completo, o `Set` procedimento tenta dividi-lo em duas partes.</span><span class="sxs-lookup"><span data-stu-id="9f615-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="9f615-153">Se ele não encontrar um espaço, ele armazena como o nome.</span><span class="sxs-lookup"><span data-stu-id="9f615-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="9f615-154">O exemplo a seguir mostra chamadas típicas para os procedimentos de propriedade `fullName`.</span><span class="sxs-lookup"><span data-stu-id="9f615-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f615-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f615-155">See Also</span></span>  
 [<span data-ttu-id="9f615-156">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="9f615-156">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="9f615-157">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="9f615-157">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="9f615-158">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="9f615-158">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="9f615-159">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="9f615-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="9f615-160">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f615-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="9f615-161">Como criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="9f615-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="9f615-162">Como chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="9f615-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="9f615-163">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f615-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="9f615-164">Como inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="9f615-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 <span data-ttu-id="9f615-165">Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="9f615-165">[How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
