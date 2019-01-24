---
title: Procedimentos de propriedade (Visual Basic)
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
ms.openlocfilehash: e61cf907ac2c5c04aa86c03a73bda7fcfcb8122d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710476"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="57c5d-102">Procedimentos de propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57c5d-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="57c5d-103">Um procedimento de propriedade é uma série de instruções do Visual Basic que manipulam uma propriedade personalizada em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="57c5d-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="57c5d-104">Procedimentos de propriedade também são conhecidos como *acessadores de propriedade*.</span><span class="sxs-lookup"><span data-stu-id="57c5d-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="57c5d-105">Visual Basic fornece para os procedimentos de propriedade a seguir:</span><span class="sxs-lookup"><span data-stu-id="57c5d-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="57c5d-106">Um `Get` procedimento retorna o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="57c5d-107">Ele é chamado quando você acessa a propriedade em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="57c5d-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="57c5d-108">Um `Set` procedimento define uma propriedade com um valor, incluindo uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="57c5d-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="57c5d-109">Ele é chamado quando você atribui um valor à propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="57c5d-110">Você geralmente define procedimentos de propriedade de pares, usando o `Get` e `Set` instruções, mas você pode definir um procedimento sozinho se a propriedade é somente leitura ([instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md)) ou somente gravação ([definido Instrução](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="57c5d-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="57c5d-111">Você pode omitir as `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="57c5d-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="57c5d-112">Para obter mais informações, consulte [Propriedades autoimplementadas](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="57c5d-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="57c5d-113">Você pode definir propriedades nas classes, estruturas e módulos.</span><span class="sxs-lookup"><span data-stu-id="57c5d-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="57c5d-114">As propriedades são `Public` por padrão, que significa que você pode chamá-los de qualquer lugar em seu aplicativo que possa acessar o recipiente da propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="57c5d-115">Para obter uma comparação entre propriedades e variáveis, consulte [diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="57c5d-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="57c5d-116">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="57c5d-116">Declaration Syntax</span></span>  
 <span data-ttu-id="57c5d-117">Uma propriedade em si é definida por um bloco de código entre o [instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) e o `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="57c5d-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="57c5d-118">Dentro desse bloco, cada procedimento de propriedade aparece como um bloco interno incluído dentro de uma instrução de declaração (`Get` ou `Set`) e a correspondência `End` declaração.</span><span class="sxs-lookup"><span data-stu-id="57c5d-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="57c5d-119">A sintaxe para declarar uma propriedade e seus procedimentos é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="57c5d-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
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
  
 <span data-ttu-id="57c5d-120">O `Modifiers` pode especificar o nível de acesso e informações sobre a sobrecarga, substituindo, compartilhando e sombreamento, bem como se a propriedade é somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="57c5d-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="57c5d-121">O `AccessLevel` sobre o `Get` ou `Set` procedimento pode ser qualquer nível que é mais restritivo que o nível de acesso especificado para a propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="57c5d-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="57c5d-122">Para obter mais informações, consulte [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57c5d-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="57c5d-123">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="57c5d-123">Data Type</span></span>  
 <span data-ttu-id="57c5d-124">Tipo de dados da propriedade e o nível de acesso principal são definidos na `Property` instrução, não nos procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="57c5d-125">Uma propriedade pode ter apenas um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="57c5d-125">A property can have only one data type.</span></span> <span data-ttu-id="57c5d-126">Por exemplo, você não pode definir uma propriedade para armazenar um `Decimal` valor, mas recuperar um `Double` valor.</span><span class="sxs-lookup"><span data-stu-id="57c5d-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="57c5d-127">Nível de acesso</span><span class="sxs-lookup"><span data-stu-id="57c5d-127">Access Level</span></span>  
 <span data-ttu-id="57c5d-128">No entanto, você pode definir um nível de acesso à entidade para uma propriedade e restringir ainda mais o nível de acesso em um dos seus procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="57c5d-129">Por exemplo, você pode definir um `Public` propriedade e, em seguida, definir um `Private Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="57c5d-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="57c5d-130">O `Get` procedimento permanece `Public`.</span><span class="sxs-lookup"><span data-stu-id="57c5d-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="57c5d-131">Você pode alterar o nível de acesso em apenas um dos procedimentos de uma propriedade e somente pode torná-lo mais restritivo do que o nível de acesso principal.</span><span class="sxs-lookup"><span data-stu-id="57c5d-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="57c5d-132">Para obter mais informações, confira [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="57c5d-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="57c5d-133">Declaração de parâmetro</span><span class="sxs-lookup"><span data-stu-id="57c5d-133">Parameter Declaration</span></span>  
 <span data-ttu-id="57c5d-134">Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md), exceto que o mecanismo de passagem deve ser `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="57c5d-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="57c5d-135">A sintaxe para cada parâmetro na lista de parâmetros é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="57c5d-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="57c5d-136">Se o parâmetro é opcional, você também deve fornecer um valor padrão como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="57c5d-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="57c5d-137">A sintaxe para especificar um valor padrão é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="57c5d-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="57c5d-138">Valor de propriedade</span><span class="sxs-lookup"><span data-stu-id="57c5d-138">Property Value</span></span>  
 <span data-ttu-id="57c5d-139">Em um `Get` procedimento, o valor retornado é fornecido para a expressão de chamada como o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="57c5d-140">Em um `Set` procedimento, o novo valor da propriedade é passado para o parâmetro do `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="57c5d-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="57c5d-141">Se você declarar explicitamente um parâmetro, você deve declará-la com o mesmo tipo de dados como a propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="57c5d-142">Se você não declarar um parâmetro, o compilador usa o parâmetro implícito `Value` para representar o novo valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="57c5d-143">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="57c5d-143">Calling Syntax</span></span>  
 <span data-ttu-id="57c5d-144">Você invoca um procedimento de propriedade implicitamente fazendo referência à propriedade.</span><span class="sxs-lookup"><span data-stu-id="57c5d-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="57c5d-145">Use o nome da propriedade da mesma maneira que você usaria o nome de uma variável, exceto que você deve fornecer valores para todos os argumentos que não são opcionais e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="57c5d-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="57c5d-146">Se nenhum argumento for fornecido, você pode, opcionalmente, omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="57c5d-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="57c5d-147">A sintaxe para uma chamada implícita para um `Set` procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="57c5d-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="57c5d-148">A sintaxe para uma chamada implícita para um `Get` procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="57c5d-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="57c5d-149">Ilustração da declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="57c5d-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="57c5d-150">A propriedade a seguir armazena um nome completo como dois nomes constituintes, o nome e o sobrenome.</span><span class="sxs-lookup"><span data-stu-id="57c5d-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="57c5d-151">Quando o código de chamada lê `fullName`, o `Get` procedimento combina as duas partes e retorna o nome completo.</span><span class="sxs-lookup"><span data-stu-id="57c5d-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="57c5d-152">Quando o código de chamada atribui um novo nome completo, o `Set` procedimento tenta dividi-lo em duas partes.</span><span class="sxs-lookup"><span data-stu-id="57c5d-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="57c5d-153">Se não encontrar um espaço, ele armazena tudo como o nome.</span><span class="sxs-lookup"><span data-stu-id="57c5d-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="57c5d-154">O exemplo a seguir mostra chamadas típicas para os procedimentos de propriedade de `fullName`.</span><span class="sxs-lookup"><span data-stu-id="57c5d-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="57c5d-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57c5d-155">See also</span></span>
- [<span data-ttu-id="57c5d-156">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="57c5d-156">Procedures</span></span>](./index.md)
- [<span data-ttu-id="57c5d-157">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="57c5d-157">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="57c5d-158">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="57c5d-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="57c5d-159">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="57c5d-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="57c5d-160">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57c5d-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="57c5d-161">Como: Criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="57c5d-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="57c5d-162">Como: Chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="57c5d-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="57c5d-163">Como: Declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57c5d-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="57c5d-164">Como: Inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="57c5d-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="57c5d-165">Como: Obter um valor de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="57c5d-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
