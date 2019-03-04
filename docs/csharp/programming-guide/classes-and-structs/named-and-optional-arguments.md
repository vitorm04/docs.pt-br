---
title: Argumentos nomeados e opcionais – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: d31cec602516b7cf3e4b358fa4b3f10e167e6e17
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202724"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="b0342-102">Argumentos nomeados e opcionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b0342-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] <span data-ttu-id="b0342-103">apresenta argumentos nomeados e opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-103">introduces named and optional arguments.</span></span> <span data-ttu-id="b0342-104">*Argumentos nomeados* permitem especificar um argumento para um parâmetro específico associando o argumento ao nome do parâmetro e não com à posição do parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b0342-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="b0342-105">*Argumentos opcionais* permitem omitir argumentos para alguns parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b0342-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="b0342-106">Ambas as técnicas podem ser usadas com os métodos, indexadores, construtores e delegados.</span><span class="sxs-lookup"><span data-stu-id="b0342-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="b0342-107">Quando você usa argumentos nomeados e opcionais, os argumentos são avaliados na ordem em que aparecem na lista de argumentos e não na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b0342-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="b0342-108">Os parâmetros nomeados e opcionais, quando usados em conjunto, permitem que você forneça argumentos para apenas alguns parâmetros de uma lista de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="b0342-109">Essa capacidade facilita bastante a chamadas para interfaces COM como as APIs de Automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="b0342-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="b0342-110">Argumentos nomeados</span><span class="sxs-lookup"><span data-stu-id="b0342-110">Named Arguments</span></span>  
 <span data-ttu-id="b0342-111">Os argumentos nomeados liberam você da necessidade de lembrar ou procurar a ordem dos parâmetros nas listas de parâmetros de métodos chamados.</span><span class="sxs-lookup"><span data-stu-id="b0342-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="b0342-112">O parâmetro para cada argumento pode ser especificado pelo nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b0342-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="b0342-113">Por exemplo, uma função que imprime detalhes de pedidos (como o nome do vendedor, nome do produto e número do pedido) pode ser chamada da maneira padrão, por meio do envio de argumentos por posição, na ordem definida pela função.</span><span class="sxs-lookup"><span data-stu-id="b0342-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="b0342-114">Se não se lembrar da ordem dos parâmetros, mas souber os nomes, você poderá enviar os argumentos em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="b0342-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="b0342-115">Os argumentos nomeados também melhoram a legibilidade do código identificando o que cada argumento representa.</span><span class="sxs-lookup"><span data-stu-id="b0342-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="b0342-116">No método de exemplo abaixo, o `sellerName` não pode ser nulo ou um espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="b0342-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="b0342-117">Como `sellerName` e `productName` são tipos de cadeia de caracteres, em vez de enviar argumentos por posição, é melhor usar argumentos nomeados para remover a ambiguidade dos dois e reduzir a confusão para qualquer pessoa que leia o código.</span><span class="sxs-lookup"><span data-stu-id="b0342-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="b0342-118">Os argumentos nomeados, quando usados com argumentos posicionais, são válidos, desde que</span><span class="sxs-lookup"><span data-stu-id="b0342-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="b0342-119">não sejam seguidos por argumentos posicionais ou,</span><span class="sxs-lookup"><span data-stu-id="b0342-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="b0342-120">_começando com o C# 7.2_, sejam usados na posição correta.</span><span class="sxs-lookup"><span data-stu-id="b0342-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="b0342-121">No exemplo a seguir, o parâmetro `orderNum` está na posição correta, mas não está explicitamente nomeado.</span><span class="sxs-lookup"><span data-stu-id="b0342-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="b0342-122">No entanto, argumentos nomeados fora de ordem serão inválidos se estiverem seguidos por argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="b0342-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0342-123">Example</span></span>  
 <span data-ttu-id="b0342-124">O código a seguir implementa os exemplos desta seção, juntamente com outros exemplos.</span><span class="sxs-lookup"><span data-stu-id="b0342-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="b0342-125">Argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="b0342-125">Optional Arguments</span></span>  
 <span data-ttu-id="b0342-126">A definição de um método, construtor, indexador ou delegado pode especificar que seus parâmetros são obrigatórios ou que são opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="b0342-127">Qualquer chamada deve fornecer argumentos para todos os parâmetros necessários, mas pode omitir argumentos para parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="b0342-128">Cada parâmetro opcional tem um valor padrão como parte de sua definição.</span><span class="sxs-lookup"><span data-stu-id="b0342-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="b0342-129">Se nenhum argumento é enviado para esse parâmetro, o valor padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="b0342-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="b0342-130">Um valor padrão deve ser um dos seguintes tipos de expressões:</span><span class="sxs-lookup"><span data-stu-id="b0342-130">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="b0342-131">uma expressão de constante;</span><span class="sxs-lookup"><span data-stu-id="b0342-131">a constant expression;</span></span>  
  
-   <span data-ttu-id="b0342-132">uma expressão da forma `new ValType()`, em que `ValType` é um tipo de valor, como um [enum](../../../csharp/language-reference/keywords/enum.md) ou um [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="b0342-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="b0342-133">uma expressão da forma [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), em que `ValType` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="b0342-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="b0342-134">Os parâmetros opcionais são definidos no final da lista de parâmetros, depois de todos os parâmetros obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b0342-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="b0342-135">Se o chamador fornecer um argumento para qualquer um de uma sucessão de parâmetros opcionais, ele deverá fornecer argumentos para todos os parâmetros opcionais anteriores.</span><span class="sxs-lookup"><span data-stu-id="b0342-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="b0342-136">Não há suporte para intervalos separados por vírgula na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="b0342-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="b0342-137">Por exemplo, no código a seguir, método de instância `ExampleMethod` está definido com um parâmetro obrigatório e dois opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="b0342-138">A chamada para `ExampleMethod` a seguir causa um erro do compilador, porque um argumento é fornecido para o terceiro parâmetro, mas não para o segundo.</span><span class="sxs-lookup"><span data-stu-id="b0342-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="b0342-139">No entanto, se você souber o nome do terceiro parâmetro, poderá usar um argumento nomeado para realizar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="b0342-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="b0342-140">O IntelliSense usa colchetes para indicar parâmetros opcionais, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0342-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b0342-141">![Informações rápidas do IntelliSense para o método ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="b0342-141">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="b0342-142">Parâmetros opcionais no ExampleMethod</span><span class="sxs-lookup"><span data-stu-id="b0342-142">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0342-143">Você também pode declarar parâmetros opcionais usando a classe <xref:System.Runtime.InteropServices.OptionalAttribute> do .NET.</span><span class="sxs-lookup"><span data-stu-id="b0342-143">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="b0342-144">Os parâmetros `OptionalAttribute` não exigem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="b0342-144">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0342-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0342-145">Example</span></span>  
 <span data-ttu-id="b0342-146">No exemplo a seguir, o construtor para `ExampleClass` tem um parâmetro, que é opcional.</span><span class="sxs-lookup"><span data-stu-id="b0342-146">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="b0342-147">O método de instância `ExampleMethod` tem um parâmetro obrigatório, `required` e dois parâmetros opcionais, `optionalstr` e `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="b0342-147">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="b0342-148">O código em `Main` mostra as diferentes maneiras como o construtor e o método podem ser invocados.</span><span class="sxs-lookup"><span data-stu-id="b0342-148">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="b0342-149">Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="b0342-149">COM Interfaces</span></span>  
 <span data-ttu-id="b0342-150">Os argumentos nomeados e opcionais, juntamente com suporte para objetos dinâmicos e outros aprimoramentos, aprimoram enormemente a interoperabilidade com APIs COM, como APIs de Automação do Office.</span><span class="sxs-lookup"><span data-stu-id="b0342-150">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="b0342-151">Por exemplo, o método <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> na interface <xref:Microsoft.Office.Interop.Excel.Range> do Microsoft Office Excel tem sete parâmetros, todos opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0342-151">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="b0342-152">Esses parâmetros são mostrados na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0342-152">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b0342-153">![Informações rápidas do IntelliSense para o método AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="b0342-153">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="b0342-154">Parâmetros de AutoFormat</span><span class="sxs-lookup"><span data-stu-id="b0342-154">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="b0342-155">No C# 3.0 e versões anteriores, é necessário um argumento para cada parâmetro, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0342-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="b0342-156">No entanto, você pode simplificar muito a chamada para `AutoFormat` usando argumentos nomeados e opcionais, introduzidos no C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="b0342-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="b0342-157">Os argumentos nomeados e opcionais permitem que você omita o argumento para um parâmetro opcional se não desejar alterar o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b0342-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="b0342-158">Na chamada a seguir, um valor é especificado para apenas um dos sete parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b0342-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="b0342-159">Para obter mais informações e exemplos, confira [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) e [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b0342-159">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="b0342-160">Resolução de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="b0342-160">Overload Resolution</span></span>  
 <span data-ttu-id="b0342-161">O uso de argumentos nomeados e opcionais afeta a resolução de sobrecarga das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="b0342-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="b0342-162">Um método, indexador ou construtor é um candidato para a execução se cada um dos parâmetros é opcional ou corresponde, por nome ou posição, a um único argumento na instrução de chamada e esse argumento pode ser convertido para o tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b0342-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="b0342-163">Se mais de um candidato for encontrado, as regras de resolução de sobrecarga de conversões preferenciais serão aplicadas aos argumentos que são especificados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="b0342-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="b0342-164">Os argumentos omitidos para parâmetros opcionais são ignorados.</span><span class="sxs-lookup"><span data-stu-id="b0342-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="b0342-165">Se dois candidatos são considerados igualmente bons, a preferência vai para um candidato que não tem parâmetros opcionais para os quais argumentos foram omitidos na chamada.</span><span class="sxs-lookup"><span data-stu-id="b0342-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="b0342-166">Esta é uma consequência da preferência geral na resolução de sobrecarga de candidatos que têm menos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b0342-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b0342-167">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b0342-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0342-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0342-168">See also</span></span>

- [<span data-ttu-id="b0342-169">Como: usar argumentos nomeados e opcionais na programação do Office</span><span class="sxs-lookup"><span data-stu-id="b0342-169">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="b0342-170">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="b0342-170">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="b0342-171">Usando construtores</span><span class="sxs-lookup"><span data-stu-id="b0342-171">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [<span data-ttu-id="b0342-172">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="b0342-172">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
