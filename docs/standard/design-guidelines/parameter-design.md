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
ms.openlocfilehash: a639e1389d0771dfcb5635b7d78982150b684fd3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150798"
---
# <a name="parameter-design"></a><span data-ttu-id="6fe1a-102">Design de parâmetro</span><span class="sxs-lookup"><span data-stu-id="6fe1a-102">Parameter Design</span></span>
<span data-ttu-id="6fe1a-103">Esta seção fornece diretrizes amplas sobre design de parâmetro, incluindo seções com as diretrizes para a verificação de argumentos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="6fe1a-104">Além disso, você deve consultar as diretrizes descritas em [parâmetros de nomeação](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6fe1a-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="6fe1a-105">**✓ DO** usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="6fe1a-106">Por exemplo, suponha que você deseja criar um método que enumera uma coleção e imprime a cada item no console.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="6fe1a-107">Esse tipo de método deve levar <xref:System.Collections.IEnumerable> como o parâmetro, não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="6fe1a-108">**X DO NOT** usar parâmetros reservados.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-109">Se mais entradas para um membro é necessária em qualquer versão futura, uma nova sobrecarga pode ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="6fe1a-110">**X DO NOT** publicamente expor métodos que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-111">Ponteiros e matrizes multidimensionais são relativamente difícil de usar adequadamente.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="6fe1a-112">Quase todos os casos, as APIs pode ser reprojetadas para evitar colocar esses tipos como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-113">**✓ DO** colocar todos os `out` parâmetros após todos o por valor e `ref` parâmetros (excluindo matrizes de parâmetros), mesmo se ele resulta em uma inconsistência no parâmetro ordenação entre sobrecargas (consulte [membro Sobrecarga](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="6fe1a-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="6fe1a-114">O `out` parâmetros podem ser vistos como valores de retorno extra e agrupando-os torna mais fácil de entender a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="6fe1a-115">**✓ DO** seja consistente em nomes de parâmetros ao substituir membros ou implementar membros de interface.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="6fe1a-116">Isso se comunica melhor a relação entre os métodos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="6fe1a-117">Escolhendo entre o Enum e parâmetros booleanos</span><span class="sxs-lookup"><span data-stu-id="6fe1a-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="6fe1a-118">**✓ DO** usar enums se um membro tivesse dois ou mais parâmetros booleanos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-119">**X DO NOT** usar valores booleanos, a menos que você tiver certeza absoluta nunca haverá a necessidade de mais de dois valores.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="6fe1a-120">Enums dão espaço para futura inclusão dos valores, mas você deve estar ciente das implicações de adicionar valores a enums, que são descritos em [Design de enumeração](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="6fe1a-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="6fe1a-121">**✓ CONSIDER** usando boolianos para parâmetros de construtor que são valores de dois estados realmente e são usados simplesmente para inicializar propriedades Boolianas.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="6fe1a-122">Validando argumentos</span><span class="sxs-lookup"><span data-stu-id="6fe1a-122">Validating Arguments</span></span>  
 <span data-ttu-id="6fe1a-123">**✓ DO** validar argumentos passados para membros públicos, protegidos ou implementados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="6fe1a-124">Lançar <xref:System.ArgumentException?displayProperty=nameWithType>, ou uma de suas subclasses, se a validação falhar.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="6fe1a-125">Observe que a validação real não necessariamente precisa acontecer no membro público ou protegido em si.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="6fe1a-126">Isso poderia acontecer em um nível inferior em alguma rotina privado ou interno.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="6fe1a-127">O ponto principal é que a área da superfície inteira que é exposta aos usuários finais verifica os argumentos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="6fe1a-128">**✓ DO** gerar <xref:System.ArgumentNullException> se um argumento nulo é passado e o membro não oferece suporte a argumentos nulos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="6fe1a-129">**✓ DO** validar parâmetros de enum.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-130">Não suponha enum argumentos serão no intervalo definido pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="6fe1a-131">O CLR permite converter qualquer valor inteiro em um valor de enumeração, mesmo se o valor não está definido na enumeração.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="6fe1a-132">**X DO NOT** usar <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para o intervalo de enum verifica.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="6fe1a-133">**✓ DO** Lembre-se de que os argumentos mutáveis podem ter alterado depois que eles foram validados.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="6fe1a-134">Se o membro é sensível à segurança, você é incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="6fe1a-135">Passagem de parâmetro</span><span class="sxs-lookup"><span data-stu-id="6fe1a-135">Parameter Passing</span></span>  
 <span data-ttu-id="6fe1a-136">Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros de, pelo valor `ref` parâmetros, e `out` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-137">Quando um argumento é passado por meio de um parâmetro por valor, o membro recebe uma cópia do argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="6fe1a-138">Se o argumento for um tipo de valor, uma cópia do argumento é colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="6fe1a-139">Se o argumento for um tipo de referência, uma cópia da referência será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="6fe1a-140">Linguagens mais populares de CLR, como c#, VB.NET e C++, padrão para passar parâmetros por valor.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="6fe1a-141">Quando um argumento é passado por meio de um `ref` parâmetro, o membro recebe uma referência para o argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="6fe1a-142">Se o argumento for um tipo de valor, uma referência para o argumento é colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="6fe1a-143">Se o argumento for um tipo de referência, uma referência para a referência será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="6fe1a-144">`Ref` parâmetros podem ser usados para permitir que o membro modificar os argumentos passados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="6fe1a-145">`Out` parâmetros são semelhantes aos `ref` parâmetros, com algumas pequenas diferenças.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="6fe1a-146">O parâmetro inicialmente é considerado não atribuídos e não pode ser lido no corpo do membro antes que ele seja atribuído a algum valor.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="6fe1a-147">Além disso, o parâmetro deve ser atribuído a algum valor antes de retorna o membro.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="6fe1a-148">**X AVOID** usando `out` ou `ref` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-149">Usando o `out` ou `ref` parâmetros requer experiência com ponteiros, compreensão das diferem entre tipos de valor e tipos de referência e métodos de tratamento com vários valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="6fe1a-150">Além disso, a diferença entre `out` e `ref` parâmetros não é amplamente compreendida.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="6fe1a-151">Arquitetos de estrutura criando para o público em geral não devem esperar que os usuários dominem o trabalho com `out` ou `ref` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="6fe1a-152">**X DO NOT** passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="6fe1a-153">Há algumas exceções limitadas para a regra, como um método que pode ser usado para trocar as referências.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="6fe1a-154">Membros com um número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fe1a-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="6fe1a-155">Os membros que podem levar a um número variável de argumentos são expressos, fornecendo um parâmetro de matriz.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="6fe1a-156">Por exemplo, <xref:System.String> fornece o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="6fe1a-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="6fe1a-157">Um usuário pode, em seguida, chamar o <xref:System.String.Format%2A?displayProperty=nameWithType> método, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6fe1a-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="6fe1a-158">Adicionando a palavra-chave c# param. autom a um parâmetro de matriz altera o parâmetro a um parâmetro de matriz params de chamada e fornece um atalho para a criação de uma matriz temporária.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="6fe1a-159">Isso permite que o usuário chamar o método, passando os elementos da matriz diretamente na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="6fe1a-160">Observe que a palavra-chave params pode ser adicionada somente para o último parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="6fe1a-161">**✓ CONSIDER** adicionando a palavra-chave params para parâmetros de matriz, se você espera que os usuários finais para transmitir matrizes com um pequeno número de elementos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="6fe1a-162">Se for esperado que muitos elementos serão passados em comum cenários, os usuários provavelmente não irá passar esses elementos embutidos de qualquer forma e, assim a palavra-chave params não é necessária.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="6fe1a-163">**X AVOID** usando matrizes de parâmetros se o chamador quase sempre deve ter a entrada já em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="6fe1a-164">Por exemplo, membros com os parâmetros de matriz de bytes seriam quase nunca ser chamados, passando bytes individuais.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="6fe1a-165">Por esse motivo, os parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="6fe1a-166">**X DO NOT** usar matrizes de parâmetros, se a matriz é modificada pelo membro levando o parâmetro de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="6fe1a-167">Devido ao fato de que muitos compiladores transformar os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação para a matriz serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="6fe1a-168">**✓ CONSIDER** usando a palavra-chave params em uma sobrecarga simple, mesmo se uma sobrecarga mais complexa não pode usá-lo.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="6fe1a-169">Se pergunte se os usuários seriam valor com a matriz de parâmetros em uma sobrecarga, mesmo se ele não estava em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="6fe1a-170">**✓ DO** tente parâmetros de ordem para que seja possível usar a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="6fe1a-171">**✓ CONSIDER** fornecendo sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos nas APIs de desempenho extremamente sensíveis.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="6fe1a-172">Isso torna possível para evitar a criação de objetos de matriz quando a API é chamada com um pequeno número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="6fe1a-173">Os nomes dos parâmetros de formulário utilizando uma forma singular do parâmetro de matriz e adicionando um sufixo numérico.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="6fe1a-174">Você deve fazer isso somente se você for para casos especiais o caminho de código inteiro, não apenas criar uma matriz e chame o método mais geral.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="6fe1a-175">**✓ DO** Lembre-se de que null pode ser passado como um argumento de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="6fe1a-176">Você deve validar que a matriz não é nula antes do processamento.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="6fe1a-177">**X DO NOT** usar o `varargs` métodos, também conhecidos como o botão de reticências.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="6fe1a-178">Algumas linguagens do CLR, como C++, dar suporte a uma convenção alternativa para a passagem de listas de parâmetro de variável chamadas `varargs` métodos.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="6fe1a-179">A convenção não deve ser usada em estruturas, porque ele não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="6fe1a-180">Parâmetros de ponteiro</span><span class="sxs-lookup"><span data-stu-id="6fe1a-180">Pointer Parameters</span></span>  
 <span data-ttu-id="6fe1a-181">Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura de código gerenciado bem projetado.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="6fe1a-182">Na maioria das vezes, os ponteiros devem ser encapsulados.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="6fe1a-183">No entanto, em alguns casos, ponteiros são necessários por motivos de interoperabilidade e o uso de ponteiros em tais casos é apropriado.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="6fe1a-184">**✓ DO** fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, como ponteiros não são compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="6fe1a-185">**X AVOID** fazendo caro argumento verificação de argumentos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="6fe1a-186">**✓ DO** convenções comuns relacionados ao ponteiro durante a criação de membros com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="6fe1a-187">Por exemplo, não é necessário para passar o índice inicial, pois a aritmética de ponteiro simple pode ser usada para alcançar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="6fe1a-188">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="6fe1a-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6fe1a-189">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6fe1a-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe1a-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fe1a-190">See also</span></span>

- [<span data-ttu-id="6fe1a-191">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="6fe1a-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="6fe1a-192">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="6fe1a-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
