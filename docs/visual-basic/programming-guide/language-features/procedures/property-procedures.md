---
title: Procedimentos de propriedade
ms.date: 07/20/2015
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
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363727"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="0bbd1-102">Procedimentos de propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bbd1-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="0bbd1-103">Um procedimento de propriedade é uma série de instruções Visual Basic que manipulam uma propriedade personalizada em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="0bbd1-104">Os procedimentos de propriedade também são conhecidos como *acessadores de propriedade*.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="0bbd1-105">O Visual Basic fornece os seguintes procedimentos de propriedade:</span><span class="sxs-lookup"><span data-stu-id="0bbd1-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="0bbd1-106">Um `Get` procedimento retorna o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="0bbd1-107">Ele é chamado quando você acessa a propriedade em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="0bbd1-108">Um `Set` procedimento define uma propriedade para um valor, incluindo uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="0bbd1-109">Ele é chamado quando você atribui um valor à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="0bbd1-110">Normalmente, você define procedimentos de propriedade em pares, usando as `Get` `Set` instruções e, mas você pode definir um dos dois procedimentos sozinho se a propriedade for somente leitura ([instrução Get](../../../language-reference/statements/get-statement.md)) ou somente gravação ([instrução SET](../../../language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="0bbd1-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="0bbd1-111">Você pode omitir `Get` o `Set` procedimento e ao usar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="0bbd1-112">Para obter mais informações, consulte [Propriedades autoimplementadas](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="0bbd1-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="0bbd1-113">Você pode definir propriedades em classes, estruturas e módulos.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="0bbd1-114">As propriedades são `Public` por padrão, o que significa que você pode chamá-las de qualquer lugar em seu aplicativo que possa acessar o contêiner da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="0bbd1-115">Para obter uma comparação de propriedades e variáveis, consulte [diferenças entre propriedades e variáveis no Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="0bbd1-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="0bbd1-116">Sintaxe de declaração</span><span class="sxs-lookup"><span data-stu-id="0bbd1-116">Declaration syntax</span></span>

<span data-ttu-id="0bbd1-117">Uma propriedade em si é definida por um bloco de código incluído na [instrução de propriedade](../../../language-reference/statements/property-statement.md) e na `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="0bbd1-118">Dentro desse bloco, cada procedimento de propriedade aparece como um bloco interno entre uma instrução de declaração ( `Get` ou `Set` ) e a `End` declaração de correspondência.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="0bbd1-119">A sintaxe para declarar uma propriedade e seus procedimentos é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bbd1-119">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
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
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="0bbd1-120">O `Modifiers` pode especificar o nível de acesso e as informações sobre sobrecarga, substituição, compartilhamento e sombreamento, bem como se a propriedade é somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="0bbd1-121">O `AccessLevel` no `Get` procedimento ou `Set` pode ser qualquer nível mais restritivo do que o nível de acesso especificado para a propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="0bbd1-122">Para obter mais informações, consulte [instrução de propriedade](../../../language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0bbd1-122">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="0bbd1-123">Tipo de Dados</span><span class="sxs-lookup"><span data-stu-id="0bbd1-123">Data Type</span></span>

<span data-ttu-id="0bbd1-124">O tipo de dados de uma propriedade e o nível de acesso de entidade de segurança são definidos na `Property` instrução, não nos procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="0bbd1-125">Uma propriedade pode ter apenas um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-125">A property can have only one data type.</span></span> <span data-ttu-id="0bbd1-126">Por exemplo, você não pode definir uma propriedade para armazenar um `Decimal` valor, mas recuperar um `Double` valor.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="0bbd1-127">Nível de acesso</span><span class="sxs-lookup"><span data-stu-id="0bbd1-127">Access Level</span></span>

<span data-ttu-id="0bbd1-128">No entanto, você pode definir um nível de acesso de entidade para uma propriedade e restringir ainda mais o nível de acesso em um de seus procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="0bbd1-129">Por exemplo, você pode definir uma `Public` propriedade e, em seguida, definir um `Private Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="0bbd1-130">O `Get` procedimento permanece `Public` .</span><span class="sxs-lookup"><span data-stu-id="0bbd1-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="0bbd1-131">Você pode alterar o nível de acesso em apenas um dos procedimentos de uma propriedade e só pode torná-lo mais restritivo do que o nível de acesso de entidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="0bbd1-132">Para obter mais informações, consulte [como: declarar uma propriedade com níveis de acesso mistos](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0bbd1-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="0bbd1-133">Declaração de parâmetro</span><span class="sxs-lookup"><span data-stu-id="0bbd1-133">Parameter declaration</span></span>

<span data-ttu-id="0bbd1-134">Você declara cada parâmetro da mesma maneira que faz para [procedimentos sub](sub-procedures.md), exceto que o mecanismo de passagem deve ser `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="0bbd1-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="0bbd1-135">A sintaxe para cada parâmetro na lista de parâmetros é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bbd1-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="0bbd1-136">Se o parâmetro for opcional, você também deverá fornecer um valor padrão como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="0bbd1-137">A sintaxe para especificar um valor padrão é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bbd1-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="0bbd1-138">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="0bbd1-138">Property value</span></span>

<span data-ttu-id="0bbd1-139">Em um `Get` procedimento, o valor de retorno é fornecido para a expressão de chamada como o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="0bbd1-140">Em um `Set` procedimento, o novo valor da propriedade é passado para o parâmetro da `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="0bbd1-141">Se você declarar explicitamente um parâmetro, deverá declará-lo com o mesmo tipo de dados que a propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="0bbd1-142">Se você não declarar um parâmetro, o compilador usará o parâmetro implícito `Value` para representar o novo valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="0bbd1-143">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="0bbd1-143">Calling syntax</span></span>

<span data-ttu-id="0bbd1-144">Você invoca um procedimento de propriedade implicitamente fazendo referência à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="0bbd1-145">Você usa o nome da propriedade da mesma maneira que usaria o nome de uma variável, exceto que você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="0bbd1-146">Se nenhum argumento for fornecido, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="0bbd1-147">A sintaxe de uma chamada implícita para um `Set` procedimento é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bbd1-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="0bbd1-148">A sintaxe de uma chamada implícita para um `Get` procedimento é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bbd1-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="0bbd1-149">Ilustração de declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="0bbd1-149">Illustration of declaration and call</span></span>

<span data-ttu-id="0bbd1-150">A propriedade a seguir armazena um nome completo como dois nomes de constituintes, o primeiro nome e o sobrenome.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="0bbd1-151">Quando o código de chamada lê `fullName` , o `Get` procedimento combina os dois nomes constituintes e retorna o nome completo.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="0bbd1-152">Quando o código de chamada atribui um novo nome completo, o `Set` procedimento tenta dividi-lo em dois nomes constituintes.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="0bbd1-153">Se não encontrar um espaço, ele o armazenará como o primeiro nome.</span><span class="sxs-lookup"><span data-stu-id="0bbd1-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="0bbd1-154">O exemplo a seguir mostra as chamadas típicas para os procedimentos de propriedade de `fullName` :</span><span class="sxs-lookup"><span data-stu-id="0bbd1-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="0bbd1-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="0bbd1-155">See also</span></span>

- [<span data-ttu-id="0bbd1-156">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="0bbd1-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="0bbd1-157">Procedimentos de função</span><span class="sxs-lookup"><span data-stu-id="0bbd1-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="0bbd1-158">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="0bbd1-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="0bbd1-159">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="0bbd1-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0bbd1-160">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bbd1-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="0bbd1-161">Como criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="0bbd1-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="0bbd1-162">Como chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="0bbd1-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="0bbd1-163">Como declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bbd1-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="0bbd1-164">Como inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="0bbd1-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="0bbd1-165">Como obter um valor a partir de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="0bbd1-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
