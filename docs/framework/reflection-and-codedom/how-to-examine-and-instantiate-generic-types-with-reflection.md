---
title: "Como examinar tipos genéricos e criar instâncias deles com a reflexão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc95b8474cdf9398d5b6705cce1b98772e5add98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="84352-102">Como examinar tipos genéricos e criar instâncias deles com a reflexão</span><span class="sxs-lookup"><span data-stu-id="84352-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="84352-103">As informações sobre tipos genéricos são obtidas da mesma forma que as informações sobre os outros tipos: examinando um objeto <xref:System.Type> que representa o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="84352-104">A diferença de princípio é que um tipo genérico tem uma lista de objetos <xref:System.Type> que representam seus parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="84352-105">O primeiro procedimento nesta seção examina os tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="84352-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="84352-106">Você pode criar um objeto <xref:System.Type> que representa um tipo construído associando argumentos de tipo aos parâmetros de tipo de uma definição de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="84352-107">O segundo procedimento demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="84352-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="84352-108">Para examinar um tipo genérico e seus parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="84352-108">To examine a generic type and its type parameters</span></span>  
  
1.  <span data-ttu-id="84352-109">Obtenha uma instância de <xref:System.Type> que representa o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="84352-110">No código a seguir, o tipo é obtido usando o operador `typeof` C# (`GetType` no Visual Basic, `typeid` no Visual C++).</span><span class="sxs-lookup"><span data-stu-id="84352-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="84352-111">Consulte o tópico da classe <xref:System.Type> para encontrar outras maneiras de obter um objeto <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="84352-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="84352-112">Observe que no restante deste procedimento, o tipo está contido em um parâmetro do método chamado `t`.</span><span class="sxs-lookup"><span data-stu-id="84352-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  <span data-ttu-id="84352-113">Use a propriedade <xref:System.Type.IsGenericType%2A> para determinar se o tipo é genérico e use a propriedade <xref:System.Type.IsGenericTypeDefinition%2A> para determinar se o tipo é uma definição de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  <span data-ttu-id="84352-114">Obtenha uma matriz que contém os argumentos de tipo genérico, usando o método <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="84352-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  <span data-ttu-id="84352-115">Para cada argumento de tipo, determine se ele é um parâmetro de tipo (por exemplo, em uma definição de tipo genérico) ou um tipo que foi especificado para um parâmetro de tipo (por exemplo, em um tipo construído), usando a propriedade <xref:System.Type.IsGenericParameter%2A>.</span><span class="sxs-lookup"><span data-stu-id="84352-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  <span data-ttu-id="84352-116">No sistema de tipo, um parâmetro de tipo genérico é representado por uma instância de <xref:System.Type>, exatamente como tipos comuns são.</span><span class="sxs-lookup"><span data-stu-id="84352-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="84352-117">O código a seguir exibe a posição do nome e do parâmetro de um objeto <xref:System.Type> que representa um parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="84352-118">A posição de parâmetro é uma informação trivial aqui. Ela é mais interessante quando você está examinando um parâmetro de tipo que foi usado como um argumento de tipo de outro tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  <span data-ttu-id="84352-119">Determine a restrição de tipo base e as restrições de interface de um parâmetro de tipo genérico usando o método <xref:System.Type.GetGenericParameterConstraints%2A> para obter todas as restrições em uma única matriz.</span><span class="sxs-lookup"><span data-stu-id="84352-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="84352-120">Não há garantia de que as restrições estarão em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="84352-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  <span data-ttu-id="84352-121">Use a propriedade <xref:System.Type.GenericParameterAttributes%2A> para descobrir as restrições especiais em um parâmetro de tipo, como exigir que ele seja um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="84352-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="84352-122">A propriedade também inclui valores que representam a variação, que você pode mascarar, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84352-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  <span data-ttu-id="84352-123">Os atributos de restrição especial são sinalizadores e o mesmo sinalizador (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) que não representa restrições especiais também não representa nenhuma covariância ou contravariância.</span><span class="sxs-lookup"><span data-stu-id="84352-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="84352-124">Portanto, para testar se há alguma dessas condições, você deve usar a máscara apropriada.</span><span class="sxs-lookup"><span data-stu-id="84352-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="84352-125">Nesse caso, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> para isolar os sinalizadores de restrição especial.</span><span class="sxs-lookup"><span data-stu-id="84352-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="84352-126">Criando uma instância de um tipo genérico</span><span class="sxs-lookup"><span data-stu-id="84352-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="84352-127">Um tipo genérico é como um modelo.</span><span class="sxs-lookup"><span data-stu-id="84352-127">A generic type is like a template.</span></span> <span data-ttu-id="84352-128">Você não pode criar instâncias dele a menos que especifique tipos reais para seus parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="84352-129">Fazer isso em tempo de execução, usando reflexão, requer o método <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="84352-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="84352-130">Para criar uma instância de um tipo genérico</span><span class="sxs-lookup"><span data-stu-id="84352-130">To construct an instance of a generic type</span></span>  
  
1.  <span data-ttu-id="84352-131">Obtenha um objeto <xref:System.Type> que representa o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="84352-132">O código a seguir obtém o tipo genérico <xref:System.Collections.Generic.Dictionary%602> de duas maneiras diferentes: usando as sobrecargas de método <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> com uma cadeia de caracteres descrevendo o tipo e chamando o método <xref:System.Type.GetGenericTypeDefinition%2A> no tipo construído `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="84352-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="84352-133">O método <xref:System.Type.MakeGenericType%2A> requer uma definição de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="84352-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  <span data-ttu-id="84352-134">Crie uma matriz dos argumentos de tipo para substituir pelos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="84352-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="84352-135">A matriz deve conter o número correto de objetos <xref:System.Type>, na mesma ordem em que aparecem na lista de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="84352-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="84352-136">Nesse caso, a chave (primeiro parâmetro de tipo) é do tipo <xref:System.String> e os valores no dicionário são instâncias de uma classe chamada `Example`.</span><span class="sxs-lookup"><span data-stu-id="84352-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  <span data-ttu-id="84352-137">Chame o método <xref:System.Type.MakeGenericType%2A> para associar os argumentos de tipo para os parâmetros de tipo e criar o tipo.</span><span class="sxs-lookup"><span data-stu-id="84352-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  <span data-ttu-id="84352-138">Use a sobrecarga de método <xref:System.Activator.CreateInstance%28System.Type%29> para criar um objeto do tipo construído.</span><span class="sxs-lookup"><span data-stu-id="84352-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="84352-139">O código a seguir armazena duas instâncias da classe `Example` no objeto `Dictionary<String, Example>` resultante.</span><span class="sxs-lookup"><span data-stu-id="84352-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="84352-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84352-140">Example</span></span>  
 <span data-ttu-id="84352-141">O exemplo de código a seguir define um método `DisplayGenericType` para examinar as definições de tipo genérico e tipos construídos usados no código e exibir suas informações.</span><span class="sxs-lookup"><span data-stu-id="84352-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="84352-142">O método `DisplayGenericType` mostra como usar as propriedades <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A> e <xref:System.Type.GenericParameterPosition%2A> e o método <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="84352-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="84352-143">O exemplo também define um método `DisplayGenericParameter` para examinar um parâmetro de tipo genérico e exibir suas restrições.</span><span class="sxs-lookup"><span data-stu-id="84352-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="84352-144">O exemplo de código define um conjunto de tipos de teste, incluindo um tipo genérico que ilustra as restrições de parâmetro de tipo e mostra como exibir informações sobre esses tipos.</span><span class="sxs-lookup"><span data-stu-id="84352-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="84352-145">O exemplo cria um tipo na classe <xref:System.Collections.Generic.Dictionary%602> criando uma matriz de argumentos de tipo e chamando o método <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="84352-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="84352-146">O programa compara o objeto <xref:System.Type> criado usando <xref:System.Type.MakeGenericType%2A> com um objeto <xref:System.Type> obtido usando `typeof` (`GetType` no Visual Basic), demonstrando que são iguais.</span><span class="sxs-lookup"><span data-stu-id="84352-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="84352-147">Da mesma forma, o programa usa o método <xref:System.Type.GetGenericTypeDefinition%2A> para obter a definição de tipo genérico do tipo construído e o compara com o objeto <xref:System.Type> que representa a classe <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="84352-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84352-148">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="84352-148">Compiling the Code</span></span>  
  
-   <span data-ttu-id="84352-149">O código contém as instruções `using` C# (`Imports` no Visual Basic) necessárias para a compilação.</span><span class="sxs-lookup"><span data-stu-id="84352-149">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="84352-150">Nenhuma referência de assembly adicional é necessária.</span><span class="sxs-lookup"><span data-stu-id="84352-150">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="84352-151">Compile o código na linha de comando usando csc.exe, vbc.exe ou cl.exe.</span><span class="sxs-lookup"><span data-stu-id="84352-151">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="84352-152">Para compilar o código no Visual Studio, coloque-o em um modelo de projeto de aplicativo do console.</span><span class="sxs-lookup"><span data-stu-id="84352-152">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84352-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84352-153">See Also</span></span>  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="84352-154">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="84352-154">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [<span data-ttu-id="84352-155">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="84352-155">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="84352-156">Genéricos</span><span class="sxs-lookup"><span data-stu-id="84352-156">Generics</span></span>](../../../docs/standard/generics/index.md)
