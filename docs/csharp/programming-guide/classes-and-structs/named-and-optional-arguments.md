---
title: "Argumentos nomeados e opcionais (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: a7f05e3e0b19bf6457989f8db2b46741cf6b28c1
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="fce34-102">Argumentos nomeados e opcionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fce34-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="fce34-103"> apresenta argumentos nomeados e opcionais.</span><span class="sxs-lookup"><span data-stu-id="fce34-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="fce34-104">*Argumentos nomeados* permitem especificar um argumento para um parâmetro específico associando o argumento ao nome do parâmetro e não com à posição do parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fce34-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="fce34-105">*Argumentos opcionais* permitem omitir argumentos para alguns parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fce34-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="fce34-106">Ambas as técnicas podem ser usadas com os métodos, indexadores, construtores e delegados.</span><span class="sxs-lookup"><span data-stu-id="fce34-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="fce34-107">Quando você usa argumentos nomeados e opcionais, os argumentos são avaliados na ordem em que aparecem na lista de argumentos e não na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fce34-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="fce34-108">Os parâmetros nomeados e opcionais, quando usados em conjunto, permitem que você forneça argumentos para apenas alguns parâmetros de uma lista de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="fce34-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="fce34-109">Essa capacidade facilita bastante a chamadas para interfaces COM como as APIs de Automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="fce34-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="fce34-110">Argumentos nomeados</span><span class="sxs-lookup"><span data-stu-id="fce34-110">Named Arguments</span></span>  
 <span data-ttu-id="fce34-111">Os argumentos nomeados liberam você da necessidade de lembrar ou procurar a ordem dos parâmetros nas listas de parâmetros de métodos chamados.</span><span class="sxs-lookup"><span data-stu-id="fce34-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="fce34-112">O parâmetro para cada argumento pode ser especificado pelo nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fce34-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="fce34-113">Por exemplo, uma função que calcula o IMC (índice de massa corporal) pode ser chamada da maneira padrão enviando argumentos para peso e altura pela posição, na ordem definida pela função.</span><span class="sxs-lookup"><span data-stu-id="fce34-113">For example, a function that calculates body mass index (BMI) can be called in the standard way by sending arguments for weight and height by position, in the order defined by the function.</span></span>  
  
 `CalculateBMI(123, 64);`  
  
 <span data-ttu-id="fce34-114">Se você não lembrar a ordem dos parâmetros, mas souber os nomes, pode enviar os argumentos em qualquer ordem, peso primeiro ou altura primeiro.</span><span class="sxs-lookup"><span data-stu-id="fce34-114">If you do not remember the order of the parameters but you do know their names, you can send the arguments in either order, weight first or height first.</span></span>  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 <span data-ttu-id="fce34-115">Os argumentos nomeados também melhoram a legibilidade do código identificando o que cada argumento representa.</span><span class="sxs-lookup"><span data-stu-id="fce34-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span>  
  
 <span data-ttu-id="fce34-116">Um argumento nomeado pode seguir argumentos posicionais, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="fce34-116">A named argument can follow positional arguments, as shown here.</span></span>  
  
 `CalculateBMI(123, height: 64);`  
  
 <span data-ttu-id="fce34-117">No entanto, um argumento posicional não pode seguir um argumento nomeado.</span><span class="sxs-lookup"><span data-stu-id="fce34-117">However, a positional argument cannot follow a named argument.</span></span> <span data-ttu-id="fce34-118">A instrução a seguir causa um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="fce34-118">The following statement causes a compiler error.</span></span>  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a><span data-ttu-id="fce34-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fce34-119">Example</span></span>  
 <span data-ttu-id="fce34-120">O código a seguir implementa os exemplos desta seção.</span><span class="sxs-lookup"><span data-stu-id="fce34-120">The following code implements the examples from this section.</span></span>  
  
 <span data-ttu-id="fce34-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fce34-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span></span>  
  
## <a name="optional-arguments"></a><span data-ttu-id="fce34-122">Argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="fce34-122">Optional Arguments</span></span>  
 <span data-ttu-id="fce34-123">A definição de um método, construtor, indexador ou delegado pode especificar que seus parâmetros são obrigatórios ou que são opcionais.</span><span class="sxs-lookup"><span data-stu-id="fce34-123">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="fce34-124">Qualquer chamada deve fornecer argumentos para todos os parâmetros necessários, mas pode omitir argumentos para parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="fce34-124">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="fce34-125">Cada parâmetro opcional tem um valor padrão como parte de sua definição.</span><span class="sxs-lookup"><span data-stu-id="fce34-125">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="fce34-126">Se nenhum argumento é enviado para esse parâmetro, o valor padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="fce34-126">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="fce34-127">Um valor padrão deve ser um dos seguintes tipos de expressões:</span><span class="sxs-lookup"><span data-stu-id="fce34-127">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="fce34-128">uma expressão de constante;</span><span class="sxs-lookup"><span data-stu-id="fce34-128">a constant expression;</span></span>  
  
-   <span data-ttu-id="fce34-129">uma expressão da forma `new ValType()`, em que `ValType` é um tipo de valor, como um [enum](../../../csharp/language-reference/keywords/enum.md) ou um [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="fce34-129">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="fce34-130">uma expressão da forma [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), em que `ValType` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="fce34-130">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="fce34-131">Os parâmetros opcionais são definidos no final da lista de parâmetros, depois de todos os parâmetros obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="fce34-131">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="fce34-132">Se o chamador fornecer um argumento para qualquer um de uma sucessão de parâmetros opcionais, ele deverá fornecer argumentos para todos os parâmetros opcionais anteriores.</span><span class="sxs-lookup"><span data-stu-id="fce34-132">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="fce34-133">Não há suporte para intervalos separados por vírgula na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="fce34-133">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="fce34-134">Por exemplo, no código a seguir, método de instância `ExampleMethod` está definido com um parâmetro obrigatório e dois opcionais.</span><span class="sxs-lookup"><span data-stu-id="fce34-134">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 <span data-ttu-id="fce34-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="fce34-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="fce34-136">A chamada para `ExampleMethod` a seguir causa um erro do compilador, porque um argumento é fornecido para o terceiro parâmetro, mas não para o segundo.</span><span class="sxs-lookup"><span data-stu-id="fce34-136">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="fce34-137">No entanto, se você souber o nome do terceiro parâmetro, poderá usar um argumento nomeado para realizar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="fce34-137">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="fce34-138">O IntelliSense usa colchetes para indicar parâmetros opcionais, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fce34-138">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fce34-139">![Informações rápidas do IntelliSense para o método ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="fce34-139">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="fce34-140">Parâmetros opcionais no ExampleMethod</span><span class="sxs-lookup"><span data-stu-id="fce34-140">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fce34-141">Você também pode declarar parâmetros opcionais usando a classe <xref:System.Runtime.InteropServices.OptionalAttribute> do .NET.</span><span class="sxs-lookup"><span data-stu-id="fce34-141">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="fce34-142">Os parâmetros `OptionalAttribute` não exigem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="fce34-142">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce34-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fce34-143">Example</span></span>  
 <span data-ttu-id="fce34-144">No exemplo a seguir, o construtor para `ExampleClass` tem um parâmetro, que é opcional.</span><span class="sxs-lookup"><span data-stu-id="fce34-144">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="fce34-145">O método de instância `ExampleMethod` tem um parâmetro obrigatório, `required` e dois parâmetros opcionais, `optionalstr` e `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="fce34-145">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="fce34-146">O código em `Main` mostra as diferentes maneiras em que o construtor e o método podem ser invocados.</span><span class="sxs-lookup"><span data-stu-id="fce34-146">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 <span data-ttu-id="fce34-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="fce34-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span></span>  
  
## <a name="com-interfaces"></a><span data-ttu-id="fce34-148">Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="fce34-148">COM Interfaces</span></span>  
 <span data-ttu-id="fce34-149">Os argumentos nomeados e opcionais, juntamente com suporte para objetos dinâmicos e outros aprimoramentos, aprimoram enormemente a interoperabilidade com APIs COM, como APIs de Automação do Office.</span><span class="sxs-lookup"><span data-stu-id="fce34-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="fce34-150">Por exemplo, o método [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) na interface [Range](http://go.microsoft.com/fwlink/?LinkId=148196) do Microsoft Office Excel tem sete parâmetros, todos opcionais.</span><span class="sxs-lookup"><span data-stu-id="fce34-150">For example, the [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) method in the Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="fce34-151">Esses parâmetros são mostrados na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fce34-151">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fce34-152">![Informações rápidas do IntelliSense para o método AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="fce34-152">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="fce34-153">Parâmetros de AutoFormat</span><span class="sxs-lookup"><span data-stu-id="fce34-153">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="fce34-154">No C# 3.0 e versões anteriores, é necessário um argumento para cada parâmetro, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fce34-154">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 <span data-ttu-id="fce34-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="fce34-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span></span>  
  
 <span data-ttu-id="fce34-156">No entanto, você pode simplificar muito a chamada para `AutoFormat` usando argumentos nomeados e opcionais, introduzidos no C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="fce34-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="fce34-157">Os argumentos nomeados e opcionais permitem que você omita o argumento para um parâmetro opcional se não desejar alterar o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fce34-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="fce34-158">Na chamada a seguir, um valor é especificado para apenas um dos sete parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fce34-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 <span data-ttu-id="fce34-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="fce34-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="fce34-160">Para obter mais informações e exemplos, consulte [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) e [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="fce34-160">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="fce34-161">Resolução de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="fce34-161">Overload Resolution</span></span>  
 <span data-ttu-id="fce34-162">O uso de argumentos nomeados e opcionais afeta a resolução de sobrecarga das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="fce34-162">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="fce34-163">Um método, indexador ou construtor é um candidato para a execução se cada um dos parâmetros é opcional ou corresponde, por nome ou posição, a um único argumento na instrução de chamada e esse argumento pode ser convertido para o tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fce34-163">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="fce34-164">Se mais de um candidato for encontrado, as regras de resolução de sobrecarga de conversões preferenciais serão aplicadas aos argumentos que são especificados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fce34-164">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="fce34-165">Os argumentos omitidos para parâmetros opcionais são ignorados.</span><span class="sxs-lookup"><span data-stu-id="fce34-165">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="fce34-166">Se dois candidatos são considerados igualmente bons, a preferência vai para um candidato que não tem parâmetros opcionais para os quais argumentos foram omitidos na chamada.</span><span class="sxs-lookup"><span data-stu-id="fce34-166">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="fce34-167">Esta é uma consequência da preferência geral na resolução de sobrecarga de candidatos que têm menos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fce34-167">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fce34-168">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fce34-168">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fce34-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fce34-169">See Also</span></span>  
 <span data-ttu-id="fce34-170">[Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="fce34-170">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="fce34-171">[Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="fce34-171">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="fce34-172">[Usando construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span><span class="sxs-lookup"><span data-stu-id="fce34-172">[Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span></span>  
 [<span data-ttu-id="fce34-173">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="fce34-173">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)

