---
title: Design de parâmetro
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: KrzysztofCwalina
ms.openlocfilehash: 28b00f5911bb47536ec44b96f284e47b6c671149
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353735"
---
# <a name="parameter-design"></a><span data-ttu-id="17d58-102">Design de parâmetro</span><span class="sxs-lookup"><span data-stu-id="17d58-102">Parameter Design</span></span>
<span data-ttu-id="17d58-103">Esta seção fornece diretrizes amplas sobre o design de parâmetros, incluindo seções com diretrizes para verificar argumentos.</span><span class="sxs-lookup"><span data-stu-id="17d58-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="17d58-104">Além disso, você deve consultar as diretrizes descritas em [parâmetros de nomenclatura](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="17d58-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="17d58-105">**✓ DO** usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.</span><span class="sxs-lookup"><span data-stu-id="17d58-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="17d58-106">Por exemplo, suponha que você queira criar um método que enumere uma coleção e imprima cada item no console.</span><span class="sxs-lookup"><span data-stu-id="17d58-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="17d58-107">Esse método deve levar <xref:System.Collections.IEnumerable> como o parâmetro, não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="17d58-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="17d58-108">**X DO NOT** usar parâmetros reservados.</span><span class="sxs-lookup"><span data-stu-id="17d58-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="17d58-109">Se mais entradas para um membro forem necessárias em alguma versão futura, uma nova sobrecarga poderá ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="17d58-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="17d58-110">**X DO NOT** publicamente expor métodos que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17d58-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="17d58-111">Ponteiros e matrizes multidimensionais são relativamente difíceis de usar corretamente.</span><span class="sxs-lookup"><span data-stu-id="17d58-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="17d58-112">Em quase todos os casos, as APIs podem ser reprojetadas para evitar a criação desses tipos como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17d58-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="17d58-113">**✓ DO** colocar todos os `out` parâmetros após todos o por valor e `ref` parâmetros (excluindo matrizes de parâmetros), mesmo se ele resulta em uma inconsistência no parâmetro ordenação entre sobrecargas (consulte [membro Sobrecarga](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="17d58-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="17d58-114">Os parâmetros `out` podem ser vistos como valores de retorno extras, e agrupá-los juntos torna a assinatura do método mais fácil de entender.</span><span class="sxs-lookup"><span data-stu-id="17d58-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="17d58-115">**✓ DO** seja consistente em nomes de parâmetros ao substituir membros ou implementar membros de interface.</span><span class="sxs-lookup"><span data-stu-id="17d58-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="17d58-116">Isso comunica melhor a relação entre os métodos.</span><span class="sxs-lookup"><span data-stu-id="17d58-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="17d58-117">Escolhendo entre parâmetros de enumeração e boolianos</span><span class="sxs-lookup"><span data-stu-id="17d58-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="17d58-118">**✓ DO** usar enums se um membro tivesse dois ou mais parâmetros booleanos.</span><span class="sxs-lookup"><span data-stu-id="17d58-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="17d58-119">**X DO NOT** usar valores booleanos, a menos que você tiver certeza absoluta nunca haverá a necessidade de mais de dois valores.</span><span class="sxs-lookup"><span data-stu-id="17d58-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="17d58-120">As enumerações oferecem algum espaço para a adição futura de valores, mas você deve estar ciente de todas as implicações da adição de valores a enums, que são descritas em [design de enumeração](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="17d58-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="17d58-121">**✓ CONSIDER** usando boolianos para parâmetros de construtor que são valores de dois estados realmente e são usados simplesmente para inicializar propriedades Boolianas.</span><span class="sxs-lookup"><span data-stu-id="17d58-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="17d58-122">Validando argumentos</span><span class="sxs-lookup"><span data-stu-id="17d58-122">Validating Arguments</span></span>  
 <span data-ttu-id="17d58-123">**✓ DO** validar argumentos passados para membros públicos, protegidos ou implementados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="17d58-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="17d58-124">Gere <xref:System.ArgumentException?displayProperty=nameWithType>, ou uma de suas subclasses, se a validação falhar.</span><span class="sxs-lookup"><span data-stu-id="17d58-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="17d58-125">Observe que a validação real não precisa necessariamente acontecer no próprio membro público ou protegido.</span><span class="sxs-lookup"><span data-stu-id="17d58-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="17d58-126">Isso pode acontecer em um nível inferior em alguma rotina privada ou interna.</span><span class="sxs-lookup"><span data-stu-id="17d58-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="17d58-127">O ponto principal é que toda a área de superfície exposta aos usuários finais verifica os argumentos.</span><span class="sxs-lookup"><span data-stu-id="17d58-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="17d58-128">**✓ DO** gerar <xref:System.ArgumentNullException> se um argumento nulo é passado e o membro não oferece suporte a argumentos nulos.</span><span class="sxs-lookup"><span data-stu-id="17d58-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="17d58-129">**✓ DO** validar parâmetros de enum.</span><span class="sxs-lookup"><span data-stu-id="17d58-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="17d58-130">Não assuma que os argumentos de enumeração estarão no intervalo definido pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="17d58-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="17d58-131">O CLR permite a conversão de qualquer valor inteiro em um valor de enumeração, mesmo se o valor não estiver definido na enumeração.</span><span class="sxs-lookup"><span data-stu-id="17d58-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="17d58-132">**X DO NOT** usar <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para o intervalo de enum verifica.</span><span class="sxs-lookup"><span data-stu-id="17d58-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="17d58-133">**✓ DO** Lembre-se de que os argumentos mutáveis podem ter alterado depois que eles foram validados.</span><span class="sxs-lookup"><span data-stu-id="17d58-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="17d58-134">Se o membro for sensível à segurança, você será incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.</span><span class="sxs-lookup"><span data-stu-id="17d58-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="17d58-135">Passagem de parâmetro</span><span class="sxs-lookup"><span data-stu-id="17d58-135">Parameter Passing</span></span>  
 <span data-ttu-id="17d58-136">Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros por valor, parâmetros `ref` e parâmetros de `out`.</span><span class="sxs-lookup"><span data-stu-id="17d58-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="17d58-137">Quando um argumento é passado por um parâmetro por valor, o membro recebe uma cópia do argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="17d58-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="17d58-138">Se o argumento for um tipo de valor, uma cópia do argumento será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="17d58-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="17d58-139">Se o argumento for um tipo de referência, uma cópia da referência será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="17d58-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="17d58-140">As C#linguagens CLR mais populares, como, VB.net e C++, por padrão, passar parâmetros por valor.</span><span class="sxs-lookup"><span data-stu-id="17d58-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="17d58-141">Quando um argumento é passado através de um parâmetro `ref`, o membro recebe uma referência para o argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="17d58-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="17d58-142">Se o argumento for um tipo de valor, uma referência ao argumento será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="17d58-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="17d58-143">Se o argumento for um tipo de referência, uma referência à referência será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="17d58-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="17d58-144">parâmetros `Ref` podem ser usados para permitir que o membro modifique argumentos passados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="17d58-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="17d58-145">os parâmetros `Out` são semelhantes aos parâmetros `ref`, com algumas pequenas diferenças.</span><span class="sxs-lookup"><span data-stu-id="17d58-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="17d58-146">O parâmetro é inicialmente considerado não atribuído e não pode ser lido no corpo do membro antes de ser atribuído a um valor.</span><span class="sxs-lookup"><span data-stu-id="17d58-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="17d58-147">Além disso, o parâmetro deve ser atribuído a um valor antes que o membro seja retornado.</span><span class="sxs-lookup"><span data-stu-id="17d58-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="17d58-148">**X AVOID** usando `out` ou `ref` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17d58-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="17d58-149">Usar parâmetros `out` ou `ref` requer experiência com ponteiros, compreendendo como tipos de valor e tipos de referência diferem e manipulando métodos com vários valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="17d58-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="17d58-150">Além disso, a diferença `out` entre `ref` os parâmetros e não é amplamente compreendida.</span><span class="sxs-lookup"><span data-stu-id="17d58-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="17d58-151">Os arquitetos de estrutura que projetam para um público geral não devem esperar que os usuários façam o mestre de trabalho com parâmetros `out` ou `ref`.</span><span class="sxs-lookup"><span data-stu-id="17d58-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="17d58-152">**X DO NOT** passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="17d58-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="17d58-153">Há algumas exceções limitadas à regra, como um método que pode ser usado para alternar referências.</span><span class="sxs-lookup"><span data-stu-id="17d58-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="17d58-154">Membros com número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="17d58-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="17d58-155">Os membros que podem obter um número variável de argumentos são expressos fornecendo um parâmetro de matriz.</span><span class="sxs-lookup"><span data-stu-id="17d58-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="17d58-156">Por exemplo, <xref:System.String> fornece o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="17d58-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```csharp  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="17d58-157">Em seguida, um usuário pode chamar o método <xref:System.String.Format%2A?displayProperty=nameWithType>, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="17d58-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="17d58-158">A adição C# da palavra-chave params a um parâmetro de matriz altera o parâmetro para o chamado parâmetro de matriz params e fornece um atalho para a criação de uma matriz temporária.</span><span class="sxs-lookup"><span data-stu-id="17d58-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```csharp  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="17d58-159">Fazer isso permite que o usuário chame o método passando os elementos da matriz diretamente na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="17d58-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="17d58-160">Observe que a palavra-chave params pode ser adicionada somente ao último parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17d58-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="17d58-161">**✓ CONSIDER** adicionando a palavra-chave params para parâmetros de matriz, se você espera que os usuários finais para transmitir matrizes com um pequeno número de elementos.</span><span class="sxs-lookup"><span data-stu-id="17d58-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="17d58-162">Se for esperado que muitos elementos sejam passados em cenários comuns, os usuários provavelmente não passarão esses elementos embutidos de qualquer forma e, portanto, a palavra-chave params não será necessária.</span><span class="sxs-lookup"><span data-stu-id="17d58-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="17d58-163">**X AVOID** usando matrizes de parâmetros se o chamador quase sempre deve ter a entrada já em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="17d58-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="17d58-164">Por exemplo, os membros com parâmetros de matriz de bytes quase nunca seriam chamados passando bytes individuais.</span><span class="sxs-lookup"><span data-stu-id="17d58-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="17d58-165">Por esse motivo, os parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="17d58-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="17d58-166">**X DO NOT** usar matrizes de parâmetros, se a matriz é modificada pelo membro levando o parâmetro de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17d58-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="17d58-167">Por causa do fato de que muitos compiladores transformam os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação na matriz será perdida.</span><span class="sxs-lookup"><span data-stu-id="17d58-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="17d58-168">**✓ CONSIDER** usando a palavra-chave params em uma sobrecarga simple, mesmo se uma sobrecarga mais complexa não pode usá-lo.</span><span class="sxs-lookup"><span data-stu-id="17d58-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="17d58-169">Pergunte-se se os usuários teriam valor com a matriz params em uma sobrecarga, mesmo que não estivesse em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="17d58-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="17d58-170">**✓ DO** tente parâmetros de ordem para que seja possível usar a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="17d58-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="17d58-171">**✓ CONSIDER** fornecendo sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos nas APIs de desempenho extremamente sensíveis.</span><span class="sxs-lookup"><span data-stu-id="17d58-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="17d58-172">Isso possibilita evitar a criação de objetos de matriz quando a API é chamada com um pequeno número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="17d58-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="17d58-173">Formate os nomes dos parâmetros por meio de uma forma singular do parâmetro de matriz e adicionando um sufixo numérico.</span><span class="sxs-lookup"><span data-stu-id="17d58-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="17d58-174">Você só deve fazer isso se for para o caso especial do caminho de código inteiro, não apenas criar uma matriz e chamar o método mais geral.</span><span class="sxs-lookup"><span data-stu-id="17d58-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="17d58-175">**✓ DO** Lembre-se de que null pode ser passado como um argumento de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17d58-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="17d58-176">Você deve validar que a matriz não é nula antes do processamento.</span><span class="sxs-lookup"><span data-stu-id="17d58-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="17d58-177">**X DO NOT** usar o `varargs` métodos, também conhecidos como o botão de reticências.</span><span class="sxs-lookup"><span data-stu-id="17d58-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="17d58-178">Algumas linguagens CLR, como C++, oferecem suporte a uma convenção alternativa para passar listas de parâmetros variáveis chamadas de métodos `varargs`.</span><span class="sxs-lookup"><span data-stu-id="17d58-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="17d58-179">A Convenção não deve ser usada em estruturas, pois não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="17d58-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="17d58-180">Parâmetros do ponteiro</span><span class="sxs-lookup"><span data-stu-id="17d58-180">Pointer Parameters</span></span>  
 <span data-ttu-id="17d58-181">Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura de código gerenciada bem projetada.</span><span class="sxs-lookup"><span data-stu-id="17d58-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="17d58-182">Na maioria das vezes, os ponteiros devem ser encapsulados.</span><span class="sxs-lookup"><span data-stu-id="17d58-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="17d58-183">No entanto, em alguns casos, os ponteiros são necessários para motivos de interoperabilidade e o uso de ponteiros nesses casos é apropriado.</span><span class="sxs-lookup"><span data-stu-id="17d58-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="17d58-184">**✓ DO** fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, como ponteiros não são compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="17d58-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="17d58-185">**X AVOID** fazendo caro argumento verificação de argumentos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="17d58-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="17d58-186">**✓ DO** convenções comuns relacionados ao ponteiro durante a criação de membros com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="17d58-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="17d58-187">Por exemplo, não há necessidade de passar o índice inicial, porque a aritmética simples de ponteiro pode ser usada para atingir o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="17d58-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="17d58-188">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="17d58-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="17d58-189">*Reprinted por permissão do Pearson Education, Inc. de diretrizes de design [Framework: Convenções, idiomas e padrões para bibliotecas .NET reutilizáveis, 2ª edição @ no__t-0 por Krzysztof Cwalina e Brad Abrams, publicadas em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="17d58-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d58-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17d58-190">See also</span></span>

- [<span data-ttu-id="17d58-191">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="17d58-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="17d58-192">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="17d58-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
