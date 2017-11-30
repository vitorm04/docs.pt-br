---
title: "Design de parâmetro"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d49c4263517830f46b1416684c7d9b874cda4db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-design"></a><span data-ttu-id="ed93a-102">Design de parâmetro</span><span class="sxs-lookup"><span data-stu-id="ed93a-102">Parameter Design</span></span>
<span data-ttu-id="ed93a-103">Esta seção fornece diretrizes gerais sobre o design de parâmetro, incluindo seções com as diretrizes para a verificação de argumentos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="ed93a-104">Além disso, consulte as diretrizes descritas em [parâmetros de nomeação de](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ed93a-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="ed93a-105">**FAZER ✓** usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.</span><span class="sxs-lookup"><span data-stu-id="ed93a-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="ed93a-106">Por exemplo, suponha que você deseja criar um método que enumera uma coleção e imprime a cada item no console.</span><span class="sxs-lookup"><span data-stu-id="ed93a-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="ed93a-107">Esse método um deve levar <xref:System.Collections.IEnumerable> como o parâmetro não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="ed93a-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="ed93a-108">**X não** usar parâmetros reservados.</span><span class="sxs-lookup"><span data-stu-id="ed93a-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="ed93a-109">Se for necessário mais de entrada para um membro em alguma versão futura, pode ser adicionada uma sobrecarga de novo.</span><span class="sxs-lookup"><span data-stu-id="ed93a-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="ed93a-110">**X não** publicamente expor métodos que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="ed93a-111">Ponteiros e matrizes multidimensionais são relativamente difícil de usar corretamente.</span><span class="sxs-lookup"><span data-stu-id="ed93a-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="ed93a-112">Em quase todos os casos, APIs podem ser reprojetados para evitar deixar esses tipos como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="ed93a-113">**FAZER ✓** colocar todos os `out` parâmetros após todos o por valor e `ref` parâmetros (excluindo matrizes de parâmetros), mesmo se ele resulta em uma inconsistência no parâmetro ordenação entre sobrecargas (consulte [membro Sobrecarga](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="ed93a-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="ed93a-114">O `out` parâmetros podem ser vistos como valores de retorno extra e agrupá-los juntos torna mais fácil de entender a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="ed93a-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="ed93a-115">**FAZER ✓** seja consistente em nomes de parâmetros ao substituir membros ou implementar membros de interface.</span><span class="sxs-lookup"><span data-stu-id="ed93a-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="ed93a-116">Isso se comunica melhor a relação entre os métodos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="ed93a-117">Escolhendo entre Enum e parâmetros booleanos</span><span class="sxs-lookup"><span data-stu-id="ed93a-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="ed93a-118">**FAZER ✓** usar enums se um membro tivesse dois ou mais parâmetros booleanos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="ed93a-119">**X não** usar valores booleanos, a menos que você tiver certeza absoluta nunca haverá a necessidade de mais de dois valores.</span><span class="sxs-lookup"><span data-stu-id="ed93a-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="ed93a-120">Enums dão espaço para futura inclusão dos valores, mas você deve estar ciente das implicações de adicionar valores para enums, que são descritos em [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="ed93a-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="ed93a-121">**✓ CONSIDERE** usando boolianos para parâmetros de construtor que são valores de dois estados realmente e são usados simplesmente para inicializar propriedades Boolianas.</span><span class="sxs-lookup"><span data-stu-id="ed93a-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="ed93a-122">Validar argumentos</span><span class="sxs-lookup"><span data-stu-id="ed93a-122">Validating Arguments</span></span>  
 <span data-ttu-id="ed93a-123">**FAZER ✓** validar argumentos passados para membros públicos, protegidos ou implementados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ed93a-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="ed93a-124">Lançar <xref:System.ArgumentException?displayProperty=nameWithType>, ou uma de suas subclasses, se a validação falhar.</span><span class="sxs-lookup"><span data-stu-id="ed93a-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="ed93a-125">Observe que a validação real não precisam necessariamente acontecer no membro público ou protegido em si.</span><span class="sxs-lookup"><span data-stu-id="ed93a-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="ed93a-126">Isso pode acontecer em um nível inferior na rotina alguns privada ou interna.</span><span class="sxs-lookup"><span data-stu-id="ed93a-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="ed93a-127">O ponto principal é que a área de superfície inteira que é exposta aos usuários finais verifica se os argumentos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="ed93a-128">**FAZER ✓** gerar <xref:System.ArgumentNullException> se um argumento nulo é passado e o membro não oferece suporte a argumentos nulos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="ed93a-129">**FAZER ✓** validar parâmetros de enum.</span><span class="sxs-lookup"><span data-stu-id="ed93a-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="ed93a-130">Não suponha enum argumentos serão no intervalo definido pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="ed93a-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="ed93a-131">O CLR permite converter qualquer valor inteiro em um valor de enumeração, mesmo se o valor não está definido na enum.</span><span class="sxs-lookup"><span data-stu-id="ed93a-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="ed93a-132">**X não** usar <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para o intervalo de enum verifica.</span><span class="sxs-lookup"><span data-stu-id="ed93a-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="ed93a-133">**FAZER ✓** Lembre-se de que os argumentos mutáveis podem ter alterado depois que eles foram validados.</span><span class="sxs-lookup"><span data-stu-id="ed93a-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="ed93a-134">Se o membro for sensível à segurança, você é incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.</span><span class="sxs-lookup"><span data-stu-id="ed93a-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="ed93a-135">Passagem de parâmetro</span><span class="sxs-lookup"><span data-stu-id="ed93a-135">Parameter Passing</span></span>  
 <span data-ttu-id="ed93a-136">Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros por valor `ref` parâmetros, e `out` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="ed93a-137">Quando um argumento é passado por meio de um parâmetro por valor, o membro recebe uma cópia do argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="ed93a-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="ed93a-138">Se o argumento for um tipo de valor, uma cópia do argumento é colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="ed93a-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="ed93a-139">Se o argumento for um tipo de referência, uma cópia da referência é colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="ed93a-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="ed93a-140">Idiomas mais populares de CLR, como c#, VB.NET e C++, padrão para passar parâmetros por valor.</span><span class="sxs-lookup"><span data-stu-id="ed93a-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="ed93a-141">Quando um argumento é passado por meio de um `ref` parâmetro, o membro recebe uma referência para o argumento passado.</span><span class="sxs-lookup"><span data-stu-id="ed93a-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="ed93a-142">Se o argumento for um tipo de valor, uma referência para o argumento é colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="ed93a-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="ed93a-143">Se o argumento for um tipo de referência, uma referência para a referência é colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="ed93a-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="ed93a-144">`Ref`parâmetros podem ser usados para permitir que o membro modificar os argumentos passados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="ed93a-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="ed93a-145">`Out`parâmetros são semelhantes às `ref` parâmetros, com algumas pequenas diferenças.</span><span class="sxs-lookup"><span data-stu-id="ed93a-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="ed93a-146">O parâmetro é considerado inicialmente não atribuídos e não pode ser lido no corpo do membro antes de ser atribuído um valor.</span><span class="sxs-lookup"><span data-stu-id="ed93a-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="ed93a-147">Além disso, o parâmetro deve ser atribuído um valor antes de retorna o membro.</span><span class="sxs-lookup"><span data-stu-id="ed93a-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="ed93a-148">**X Evite** usando `out` ou `ref` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="ed93a-149">Usando `out` ou `ref` parâmetros requer experiência com ponteiros, compreender a diferença entre tipos de valor e tipos de referência e tratamento de métodos com vários valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="ed93a-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="ed93a-150">Além disso, a diferença entre `out` e `ref` parâmetros não é compreendido amplamente.</span><span class="sxs-lookup"><span data-stu-id="ed93a-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="ed93a-151">Arquitetos de estrutura criando para o público em geral não devem esperar que os usuários mestre trabalhar com `out` ou `ref` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="ed93a-152">**X não** passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="ed93a-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="ed93a-153">Há algumas exceções limitadas para a regra, como um método que pode ser usada para trocar as referências.</span><span class="sxs-lookup"><span data-stu-id="ed93a-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="ed93a-154">Membros com um número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed93a-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="ed93a-155">Membros que podem levar a um número variável de argumentos são expressos, fornecendo um parâmetro de matriz.</span><span class="sxs-lookup"><span data-stu-id="ed93a-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="ed93a-156">Por exemplo, <xref:System.String> fornece o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="ed93a-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="ed93a-157">Um usuário pode chamar o <xref:System.String.Format%2A?displayProperty=nameWithType> método, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ed93a-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="ed93a-158">Adicionando a palavra-chave c# parâmetros para um parâmetro de matriz altera o parâmetro para um parâmetro de matriz de parâmetros chamados e fornece um atalho para a criação de uma matriz temporária.</span><span class="sxs-lookup"><span data-stu-id="ed93a-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="ed93a-159">Isso permite que o usuário chamar o método, passando os elementos da matriz diretamente na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="ed93a-160">Observe que a palavra-chave params pode ser adicionada somente para o último parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="ed93a-161">**✓ CONSIDERE** adicionando a palavra-chave params para parâmetros de matriz, se você espera que os usuários finais para transmitir matrizes com um pequeno número de elementos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="ed93a-162">Se for esperado que muitos elementos serão passados em comum cenários, os usuários provavelmente não passar esses elementos embutidos assim mesmo e portanto a palavra-chave params não é necessária.</span><span class="sxs-lookup"><span data-stu-id="ed93a-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="ed93a-163">**X Evite** usando matrizes de parâmetros se o chamador quase sempre deve ter a entrada já em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="ed93a-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="ed93a-164">Por exemplo, membros com parâmetros da matriz de bytes quase nunca serão chamados passando bytes individuais.</span><span class="sxs-lookup"><span data-stu-id="ed93a-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="ed93a-165">Por esse motivo, parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="ed93a-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="ed93a-166">**X não** usar matrizes de parâmetros, se a matriz é modificada pelo membro levando o parâmetro de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="ed93a-167">Devido ao fato de que muitos compiladores transformar os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação para a matriz serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="ed93a-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="ed93a-168">**✓ CONSIDERE** usando a palavra-chave params em uma sobrecarga simple, mesmo se uma sobrecarga mais complexa não pode usá-lo.</span><span class="sxs-lookup"><span data-stu-id="ed93a-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="ed93a-169">Pergunte se os usuários seriam valor com a matriz de parâmetros em uma sobrecarga, mesmo se ele não estava em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="ed93a-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="ed93a-170">**FAZER ✓** tente parâmetros de ordem para que seja possível usar a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="ed93a-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="ed93a-171">**✓ CONSIDERE** fornecendo sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos nas APIs de desempenho extremamente sensíveis.</span><span class="sxs-lookup"><span data-stu-id="ed93a-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="ed93a-172">Isso torna possível para evitar a criação de objetos da matriz quando a API é chamada com um pequeno número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="ed93a-173">Formam os nomes dos parâmetros considerando uma forma singular de parâmetro de matriz e adicionando um sufixo numérico.</span><span class="sxs-lookup"><span data-stu-id="ed93a-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="ed93a-174">Você deve fazer isso apenas se você for para casos especiais o caminho de código inteiro, não apenas criar uma matriz e chame o método mais geral.</span><span class="sxs-lookup"><span data-stu-id="ed93a-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="ed93a-175">**FAZER ✓** Lembre-se de que null pode ser passado como um argumento de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="ed93a-176">Você deve validar que a matriz não é nula antes do processamento.</span><span class="sxs-lookup"><span data-stu-id="ed93a-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="ed93a-177">**X não** usar o `varargs` métodos, também conhecidos como o botão de reticências.</span><span class="sxs-lookup"><span data-stu-id="ed93a-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="ed93a-178">Algumas linguagens CLR, como C++, dar suporte a uma convenção alternativa para a passagem de listas de parâmetros variáveis chamadas `varargs` métodos.</span><span class="sxs-lookup"><span data-stu-id="ed93a-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="ed93a-179">A convenção não deve ser usada em estruturas, porque ele não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="ed93a-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="ed93a-180">Parâmetros de ponteiro</span><span class="sxs-lookup"><span data-stu-id="ed93a-180">Pointer Parameters</span></span>  
 <span data-ttu-id="ed93a-181">Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura bem projetado de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ed93a-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="ed93a-182">Na maioria das vezes, os ponteiros devem ser encapsulados.</span><span class="sxs-lookup"><span data-stu-id="ed93a-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="ed93a-183">No entanto, em alguns casos ponteiros são necessários por motivos de interoperabilidade, e usar ponteiros nesses casos é apropriado.</span><span class="sxs-lookup"><span data-stu-id="ed93a-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="ed93a-184">**FAZER ✓** fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, como ponteiros não são compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="ed93a-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="ed93a-185">**X Evite** fazendo caro argumento verificação de argumentos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="ed93a-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="ed93a-186">**FAZER ✓** convenções comuns relacionados ao ponteiro durante a criação de membros com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="ed93a-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="ed93a-187">Por exemplo, não há nenhuma necessidade de passar o índice inicial, porque aritmética de ponteiro simple pode ser usada para obter o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="ed93a-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="ed93a-188">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="ed93a-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ed93a-189">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ed93a-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed93a-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed93a-190">See Also</span></span>  
 [<span data-ttu-id="ed93a-191">Diretrizes de Design de membro</span><span class="sxs-lookup"><span data-stu-id="ed93a-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="ed93a-192">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="ed93a-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
