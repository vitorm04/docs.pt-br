---
title: Argumentos nomeados e opcionais – Guia de Programação em C#
description: Argumentos nomeados em C# especificam argumentos por nome, não posição. Argumentos opcionais podem ser omitidos.
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
ms.openlocfilehash: 4c9c932e3df4035024c90e92e4d80309fffe3ce3
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406226"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="f502e-104">Argumentos nomeados e opcionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f502e-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="f502e-105">O C# 4 apresenta argumentos nomeados e opcionais.</span><span class="sxs-lookup"><span data-stu-id="f502e-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="f502e-106">Os *argumentos nomeados* permitem que você especifique um argumento para um parâmetro, correspondendo ao argumento com seu nome em vez de sua posição na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f502e-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="f502e-107">*Argumentos opcionais* permitem omitir argumentos para alguns parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f502e-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="f502e-108">Ambas as técnicas podem ser usadas com os métodos, indexadores, construtores e delegados.</span><span class="sxs-lookup"><span data-stu-id="f502e-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="f502e-109">Quando você usa argumentos nomeados e opcionais, os argumentos são avaliados na ordem em que aparecem na lista de argumentos e não na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f502e-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="f502e-110">Parâmetros nomeados e opcionais permitem que você forneça argumentos para os parâmetros selecionados.</span><span class="sxs-lookup"><span data-stu-id="f502e-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="f502e-111">Esse recurso facilita muito as chamadas para interfaces COM, como as APIs de automação de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f502e-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="f502e-112">Argumentos nomeados</span><span class="sxs-lookup"><span data-stu-id="f502e-112">Named Arguments</span></span>

<span data-ttu-id="f502e-113">Os argumentos nomeados liberam você da correspondência da ordem dos parâmetros nas listas de parâmetros dos métodos chamados.</span><span class="sxs-lookup"><span data-stu-id="f502e-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="f502e-114">O parâmetro para cada argumento pode ser especificado pelo nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f502e-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="f502e-115">Por exemplo, uma função que imprime detalhes do pedido (como, nome do vendedor, número do pedido & nome do produto) pode ser chamada enviando argumentos por posição, na ordem definida pela função.</span><span class="sxs-lookup"><span data-stu-id="f502e-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="f502e-116">Se você não se lembrar da ordem dos parâmetros, mas souber seus nomes, poderá enviar os argumentos em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="f502e-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="f502e-117">Os argumentos nomeados também melhoram a legibilidade do código identificando o que cada argumento representa.</span><span class="sxs-lookup"><span data-stu-id="f502e-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="f502e-118">No método de exemplo abaixo, o `sellerName` não pode ser nulo ou espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f502e-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="f502e-119">Como `sellerName` e `productName` são tipos de cadeia de caracteres, em vez de enviar argumentos por posição, é melhor usar argumentos nomeados para remover a ambiguidade dos dois e reduzir a confusão para qualquer pessoa que leia o código.</span><span class="sxs-lookup"><span data-stu-id="f502e-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="f502e-120">Os argumentos nomeados, quando usados com argumentos posicionais, são válidos, desde que</span><span class="sxs-lookup"><span data-stu-id="f502e-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="f502e-121">não sejam seguidos por argumentos posicionais ou,</span><span class="sxs-lookup"><span data-stu-id="f502e-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="f502e-122">_começando com o C# 7.2_, sejam usados na posição correta.</span><span class="sxs-lookup"><span data-stu-id="f502e-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="f502e-123">No exemplo a seguir, o parâmetro `orderNum` está na posição correta, mas não está explicitamente nomeado.</span><span class="sxs-lookup"><span data-stu-id="f502e-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="f502e-124">Argumentos posicionais que seguem os argumentos nomeados fora de ordem são inválidos.</span><span class="sxs-lookup"><span data-stu-id="f502e-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="f502e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f502e-125">Example</span></span>

<span data-ttu-id="f502e-126">O código a seguir implementa os exemplos desta seção, juntamente com outros exemplos.</span><span class="sxs-lookup"><span data-stu-id="f502e-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="f502e-127">Argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="f502e-127">Optional Arguments</span></span>

<span data-ttu-id="f502e-128">A definição de um método, Construtor, indexador ou delegado pode especificar seus parâmetros são obrigatórios ou opcionais.</span><span class="sxs-lookup"><span data-stu-id="f502e-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="f502e-129">Qualquer chamada deve fornecer argumentos para todos os parâmetros necessários, mas pode omitir argumentos para parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="f502e-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="f502e-130">Cada parâmetro opcional tem um valor padrão como parte de sua definição.</span><span class="sxs-lookup"><span data-stu-id="f502e-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="f502e-131">Se nenhum argumento é enviado para esse parâmetro, o valor padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="f502e-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="f502e-132">Um valor padrão deve ser um dos seguintes tipos de expressões:</span><span class="sxs-lookup"><span data-stu-id="f502e-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="f502e-133">uma expressão de constante;</span><span class="sxs-lookup"><span data-stu-id="f502e-133">a constant expression;</span></span>  
- <span data-ttu-id="f502e-134">uma expressão da forma `new ValType()`, em que `ValType` é um tipo de valor, como um [enum](../../language-reference/builtin-types/enum.md) ou um [struct](../../language-reference/builtin-types/struct.md);</span><span class="sxs-lookup"><span data-stu-id="f502e-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="f502e-135">uma expressão da forma [default(ValType)](../../language-reference/operators/default.md), em que `ValType` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="f502e-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="f502e-136">Os parâmetros opcionais são definidos no final da lista de parâmetros, depois de todos os parâmetros obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="f502e-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="f502e-137">Se o chamador fornecer um argumento para qualquer um de uma sucessão de parâmetros opcionais, ele deverá fornecer argumentos para todos os parâmetros opcionais anteriores.</span><span class="sxs-lookup"><span data-stu-id="f502e-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="f502e-138">Não há suporte para lacunas separadas por vírgula na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="f502e-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="f502e-139">Por exemplo, no código a seguir, método de instância `ExampleMethod` está definido com um parâmetro obrigatório e dois opcionais.</span><span class="sxs-lookup"><span data-stu-id="f502e-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="f502e-140">A chamada para `ExampleMethod` a seguir causa um erro do compilador, porque um argumento é fornecido para o terceiro parâmetro, mas não para o segundo.</span><span class="sxs-lookup"><span data-stu-id="f502e-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="f502e-141">No entanto, se você souber o nome do terceiro parâmetro, poderá usar um argumento nomeado para realizar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="f502e-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="f502e-142">O IntelliSense usa colchetes para indicar parâmetros opcionais, conforme mostrado na seguinte ilustração:</span><span class="sxs-lookup"><span data-stu-id="f502e-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![Captura de tela mostrando as Informações Rápidas do IntelliSense para o método ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="f502e-144">Você também pode declarar parâmetros opcionais usando a classe <xref:System.Runtime.InteropServices.OptionalAttribute> do .NET.</span><span class="sxs-lookup"><span data-stu-id="f502e-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="f502e-145">Os parâmetros `OptionalAttribute` não exigem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f502e-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="f502e-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f502e-146">Example</span></span>

<span data-ttu-id="f502e-147">No exemplo a seguir, o construtor para `ExampleClass` tem um parâmetro, que é opcional.</span><span class="sxs-lookup"><span data-stu-id="f502e-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="f502e-148">O método de instância `ExampleMethod` tem um parâmetro obrigatório, `required` e dois parâmetros opcionais, `optionalstr` e `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="f502e-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="f502e-149">O código em `Main` mostra as diferentes maneiras em que o construtor e o método podem ser invocados.</span><span class="sxs-lookup"><span data-stu-id="f502e-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="f502e-150">O código anterior mostra vários exemplos em que parâmetros opcionais não são aplicados corretamente.</span><span class="sxs-lookup"><span data-stu-id="f502e-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="f502e-151">O primeiro ilustra que um argumento deve ser fornecido para o primeiro parâmetro, que é necessário.</span><span class="sxs-lookup"><span data-stu-id="f502e-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="f502e-152">Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="f502e-152">COM Interfaces</span></span>

<span data-ttu-id="f502e-153">Argumentos nomeados e opcionais, juntamente com o suporte para objetos dinâmicos, melhoram muito a interoperabilidade com APIs COM, como APIs de automação do Office.</span><span class="sxs-lookup"><span data-stu-id="f502e-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="f502e-154">Por exemplo, o método <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> na interface <xref:Microsoft.Office.Interop.Excel.Range> do Microsoft Office Excel tem sete parâmetros, todos opcionais.</span><span class="sxs-lookup"><span data-stu-id="f502e-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="f502e-155">Esses parâmetros são mostrados na seguinte ilustração:</span><span class="sxs-lookup"><span data-stu-id="f502e-155">These parameters are shown in the following illustration:</span></span>

![Captura de tela mostrando as Informações Rápidas do IntelliSense para o método AutoFormat.](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="f502e-157">No C# 3.0 e versões anteriores, é necessário um argumento para cada parâmetro, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f502e-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="f502e-158">No entanto, você pode simplificar muito a chamada para `AutoFormat` usando argumentos nomeados e opcionais, introduzidos no C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="f502e-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="f502e-159">Argumentos nomeados e opcionais permitem omitir o argumento para um parâmetro opcional se você não quiser alterar o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f502e-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="f502e-160">Na chamada a seguir, um valor é especificado para apenas um dos sete parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f502e-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="f502e-161">Para obter mais informações e exemplos, consulte [como usar argumentos nomeados e opcionais na programação do Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) e [como acessar objetos de interoperabilidade do Office usando recursos do C#](../interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f502e-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="f502e-162">Resolução de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="f502e-162">Overload Resolution</span></span>

<span data-ttu-id="f502e-163">O uso de argumentos nomeados e opcionais afeta a resolução de sobrecarga das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="f502e-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="f502e-164">Um método, indexador ou construtor é um candidato para a execução se cada um dos parâmetros é opcional ou corresponde, por nome ou posição, a um único argumento na instrução de chamada e esse argumento pode ser convertido para o tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f502e-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="f502e-165">Se mais de um candidato for encontrado, as regras de resolução de sobrecarga de conversões preferenciais serão aplicadas aos argumentos que são especificados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f502e-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="f502e-166">Os argumentos omitidos para parâmetros opcionais são ignorados.</span><span class="sxs-lookup"><span data-stu-id="f502e-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="f502e-167">Se dois candidatos forem considerados bons, a preferência vai para um candidato que não tem parâmetros opcionais para os quais os argumentos foram omitidos na chamada.</span><span class="sxs-lookup"><span data-stu-id="f502e-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="f502e-168">A resolução de sobrecarga geralmente prefere candidatos com menos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f502e-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="f502e-169">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f502e-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
