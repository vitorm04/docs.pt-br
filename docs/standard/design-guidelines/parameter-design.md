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
ms.openlocfilehash: 46c1b8f03d054a63ea837a73fd30eeed163ab0a4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290091"
---
# <a name="parameter-design"></a><span data-ttu-id="c2d04-102">Design de parâmetro</span><span class="sxs-lookup"><span data-stu-id="c2d04-102">Parameter design</span></span>

<span data-ttu-id="c2d04-103">Esta seção fornece diretrizes amplas sobre o design de parâmetros, incluindo seções com diretrizes para verificar argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="c2d04-104">Além disso, você deve consultar as diretrizes descritas em [parâmetros de nomenclatura](naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c2d04-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="c2d04-105">✔️ usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.</span><span class="sxs-lookup"><span data-stu-id="c2d04-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="c2d04-106">Por exemplo, suponha que você queira criar um método que enumere uma coleção e imprima cada item no console.</span><span class="sxs-lookup"><span data-stu-id="c2d04-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="c2d04-107">Esse método deve ser adotado <xref:System.Collections.IEnumerable> como o parâmetro, não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList> , por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c2d04-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="c2d04-108">❌Não use parâmetros reservados.</span><span class="sxs-lookup"><span data-stu-id="c2d04-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="c2d04-109">Se mais entradas para um membro forem necessárias em alguma versão futura, uma nova sobrecarga poderá ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="c2d04-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="c2d04-110">❌Não têm métodos expostos publicamente que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c2d04-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="c2d04-111">Ponteiros e matrizes multidimensionais são relativamente difíceis de usar corretamente.</span><span class="sxs-lookup"><span data-stu-id="c2d04-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="c2d04-112">Em quase todos os casos, as APIs podem ser reprojetadas para evitar a criação desses tipos como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c2d04-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="c2d04-113">✔️ FAZER todos os `out` parâmetros após todos os parâmetros por valor e `ref` (excluindo matrizes de parâmetro), mesmo que resulte em uma inconsistência na ordenação de parâmetros entre sobrecargas (consulte [sobrecarga de membros](member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="c2d04-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="c2d04-114">Os `out` parâmetros podem ser vistos como valores de retorno extras e agrupá-los juntos torna a assinatura do método mais fácil de entender.</span><span class="sxs-lookup"><span data-stu-id="c2d04-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="c2d04-115">✔️ são consistentes na nomenclatura de parâmetros ao substituir membros ou implementar membros de interface.</span><span class="sxs-lookup"><span data-stu-id="c2d04-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="c2d04-116">Isso comunica melhor a relação entre os métodos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-116">This better communicates the relationship between the methods.</span></span>

### <a name="choose-between-enum-and-boolean-parameters"></a><span data-ttu-id="c2d04-117">Escolha entre parâmetros de enumeração e boolianos</span><span class="sxs-lookup"><span data-stu-id="c2d04-117">Choose between enum and boolean parameters</span></span>
 <span data-ttu-id="c2d04-118">✔️ usar enums se um membro, caso contrário, teria dois ou mais parâmetros boolianos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="c2d04-119">❌Não use boolianos, a menos que esteja absolutamente certo de que nunca haverá necessidade de mais de dois valores.</span><span class="sxs-lookup"><span data-stu-id="c2d04-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="c2d04-120">As enumerações oferecem algum espaço para a adição futura de valores, mas você deve estar ciente de todas as implicações da adição de valores a enums, que são descritas em [design de enumeração](enum.md).</span><span class="sxs-lookup"><span data-stu-id="c2d04-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="c2d04-121">✔️ Considere usar boolianos para parâmetros de construtor que são verdadeiramente valores de dois Estados e são simplesmente usados para inicializar propriedades booleanas.</span><span class="sxs-lookup"><span data-stu-id="c2d04-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validate-arguments"></a><span data-ttu-id="c2d04-122">Validar argumentos</span><span class="sxs-lookup"><span data-stu-id="c2d04-122">Validate arguments</span></span>
 <span data-ttu-id="c2d04-123">✔️ validar argumentos passados para membros públicos, protegidos ou explicitamente implementados.</span><span class="sxs-lookup"><span data-stu-id="c2d04-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="c2d04-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType> , ou uma de suas subclasses, se a validação falhar.</span><span class="sxs-lookup"><span data-stu-id="c2d04-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="c2d04-125">Observe que a validação real não precisa necessariamente acontecer no próprio membro público ou protegido.</span><span class="sxs-lookup"><span data-stu-id="c2d04-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="c2d04-126">Isso pode acontecer em um nível inferior em alguma rotina privada ou interna.</span><span class="sxs-lookup"><span data-stu-id="c2d04-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="c2d04-127">O ponto principal é que toda a área de superfície exposta aos usuários finais verifica os argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="c2d04-128">✔️ gerar <xref:System.ArgumentNullException> se um argumento nulo for passado e o membro não oferecer suporte a argumentos nulos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="c2d04-129">✔️ validar os parâmetros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c2d04-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="c2d04-130">Não assuma que os argumentos de enumeração estarão no intervalo definido pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="c2d04-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="c2d04-131">O CLR permite a conversão de qualquer valor inteiro em um valor de enumeração, mesmo se o valor não estiver definido na enumeração.</span><span class="sxs-lookup"><span data-stu-id="c2d04-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="c2d04-132">❌Não use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para verificações de intervalo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c2d04-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="c2d04-133">✔️ estar ciente de que argumentos mutáveis podem ter sido alterados depois de serem validados.</span><span class="sxs-lookup"><span data-stu-id="c2d04-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="c2d04-134">Se o membro for sensível à segurança, você será incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.</span><span class="sxs-lookup"><span data-stu-id="c2d04-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="pass-parameters"></a><span data-ttu-id="c2d04-135">Passar parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2d04-135">Pass parameters</span></span>
 <span data-ttu-id="c2d04-136">Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros por valor, `ref` parâmetros e `out` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c2d04-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="c2d04-137">Quando um argumento é passado por um parâmetro por valor, o membro recebe uma cópia do argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="c2d04-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="c2d04-138">Se o argumento for um tipo de valor, uma cópia do argumento será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d04-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="c2d04-139">Se o argumento for um tipo de referência, uma cópia da referência será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d04-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="c2d04-140">As linguagens CLR mais populares, como C#, Visual Basic e C++, assumem como padrão a passagem de parâmetros por valor.</span><span class="sxs-lookup"><span data-stu-id="c2d04-140">Most popular CLR languages, such as C#, Visual Basic, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="c2d04-141">Quando um argumento é passado por um `ref` parâmetro, o membro recebe uma referência para o argumento real passado.</span><span class="sxs-lookup"><span data-stu-id="c2d04-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="c2d04-142">Se o argumento for um tipo de valor, uma referência ao argumento será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d04-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="c2d04-143">Se o argumento for um tipo de referência, uma referência à referência será colocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d04-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="c2d04-144">`Ref`os parâmetros podem ser usados para permitir que o membro modifique os argumentos passados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="c2d04-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="c2d04-145">`Out`os parâmetros são semelhantes aos `ref` parâmetros, com algumas pequenas diferenças.</span><span class="sxs-lookup"><span data-stu-id="c2d04-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="c2d04-146">O parâmetro é inicialmente considerado não atribuído e não pode ser lido no corpo do membro antes de ser atribuído a um valor.</span><span class="sxs-lookup"><span data-stu-id="c2d04-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="c2d04-147">Além disso, o parâmetro deve ser atribuído a um valor antes que o membro seja retornado.</span><span class="sxs-lookup"><span data-stu-id="c2d04-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="c2d04-148">❌Evite usar `out` `ref` parâmetros ou.</span><span class="sxs-lookup"><span data-stu-id="c2d04-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="c2d04-149">O uso de `out` `ref` parâmetros ou requer experiência com ponteiros, compreendendo como tipos de valor e tipos de referência diferem e manipulando métodos com vários valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="c2d04-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="c2d04-150">Além disso, a diferença entre os `out` `ref` parâmetros e não é amplamente compreendida.</span><span class="sxs-lookup"><span data-stu-id="c2d04-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="c2d04-151">Os arquitetos de estrutura que projetam para um público geral não devem esperar que os usuários façam o mestre de trabalho com os `out` `ref` parâmetros ou.</span><span class="sxs-lookup"><span data-stu-id="c2d04-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="c2d04-152">❌Não passe tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="c2d04-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="c2d04-153">Há algumas exceções limitadas à regra, como um método que pode ser usado para alternar referências.</span><span class="sxs-lookup"><span data-stu-id="c2d04-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="c2d04-154">Membros com número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2d04-154">Members with variable number of parameters</span></span>
 <span data-ttu-id="c2d04-155">Os membros que podem obter um número variável de argumentos são expressos fornecendo um parâmetro de matriz.</span><span class="sxs-lookup"><span data-stu-id="c2d04-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="c2d04-156">Por exemplo, <xref:System.String> o fornece o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="c2d04-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="c2d04-157">Um usuário pode então chamar o <xref:System.String.Format%2A?displayProperty=nameWithType> método, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2d04-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="c2d04-158">Adicionar a palavra-chave Parameters do C# a um parâmetro de matriz altera o parâmetro para o chamado parâmetro de matriz params e fornece um atalho para a criação de uma matriz temporária.</span><span class="sxs-lookup"><span data-stu-id="c2d04-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="c2d04-159">Fazer isso permite que o usuário chame o método passando os elementos da matriz diretamente na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="c2d04-160">Observe que a palavra-chave params pode ser adicionada somente ao último parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c2d04-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="c2d04-161">✔️ Considere adicionar a palavra-chave params aos parâmetros de matriz se você espera que os usuários finais passem matrizes com um pequeno número de elementos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="c2d04-162">Se for esperado que muitos elementos sejam passados em cenários comuns, os usuários provavelmente não passarão esses elementos embutidos de qualquer forma e, portanto, a palavra-chave params não será necessária.</span><span class="sxs-lookup"><span data-stu-id="c2d04-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="c2d04-163">❌Evite usar matrizes params se o chamador quase sempre tiver a entrada já em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c2d04-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="c2d04-164">Por exemplo, os membros com parâmetros de matriz de bytes quase nunca seriam chamados passando bytes individuais.</span><span class="sxs-lookup"><span data-stu-id="c2d04-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="c2d04-165">Por esse motivo, os parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="c2d04-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="c2d04-166">❌Não use matrizes params se a matriz for modificada pelo membro usando o parâmetro de matriz params.</span><span class="sxs-lookup"><span data-stu-id="c2d04-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="c2d04-167">Por causa do fato de que muitos compiladores transformam os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação na matriz será perdida.</span><span class="sxs-lookup"><span data-stu-id="c2d04-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="c2d04-168">✔️ Considere usar a palavra-chave params em uma sobrecarga simples, mesmo se uma sobrecarga mais complexa não puder usá-la.</span><span class="sxs-lookup"><span data-stu-id="c2d04-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="c2d04-169">Pergunte-se se os usuários teriam valor com a matriz params em uma sobrecarga, mesmo que não estivesse em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="c2d04-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>

 <span data-ttu-id="c2d04-170">✔️ Tente ordenar os parâmetros para tornar possível usar a palavra-chave params.</span><span class="sxs-lookup"><span data-stu-id="c2d04-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="c2d04-171">✔️ Considere fornecer sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos em APIs extremamente sensíveis ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="c2d04-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="c2d04-172">Isso possibilita evitar a criação de objetos de matriz quando a API é chamada com um pequeno número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="c2d04-173">Formate os nomes dos parâmetros por meio de uma forma singular do parâmetro de matriz e adicionando um sufixo numérico.</span><span class="sxs-lookup"><span data-stu-id="c2d04-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="c2d04-174">Você só deve fazer isso se for para o caso especial do caminho de código inteiro, não apenas criar uma matriz e chamar o método mais geral.</span><span class="sxs-lookup"><span data-stu-id="c2d04-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="c2d04-175">✔️ estar ciente de que NULL pode ser passado como um argumento de matriz params.</span><span class="sxs-lookup"><span data-stu-id="c2d04-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="c2d04-176">Você deve validar que a matriz não é nula antes do processamento.</span><span class="sxs-lookup"><span data-stu-id="c2d04-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="c2d04-177">❌Não use os `varargs` métodos, caso contrário, conhecidos como reticências.</span><span class="sxs-lookup"><span data-stu-id="c2d04-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="c2d04-178">Algumas linguagens CLR, como C++, dão suporte a uma convenção alternativa para passar listas de parâmetros de variáveis chamados `varargs` métodos.</span><span class="sxs-lookup"><span data-stu-id="c2d04-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="c2d04-179">A Convenção não deve ser usada em estruturas, pois não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="c2d04-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="c2d04-180">Parâmetros do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c2d04-180">Pointer parameters</span></span>
 <span data-ttu-id="c2d04-181">Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura de código gerenciada bem projetada.</span><span class="sxs-lookup"><span data-stu-id="c2d04-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="c2d04-182">Na maioria das vezes, os ponteiros devem ser encapsulados.</span><span class="sxs-lookup"><span data-stu-id="c2d04-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="c2d04-183">No entanto, em alguns casos, os ponteiros são necessários para motivos de interoperabilidade e o uso de ponteiros nesses casos é apropriado.</span><span class="sxs-lookup"><span data-stu-id="c2d04-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="c2d04-184">✔️ fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, porque os ponteiros não são compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="c2d04-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="c2d04-185">❌Evite fazer uma verificação cara de argumento dos argumentos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c2d04-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="c2d04-186">✔️ seguir Convenções comuns relacionadas a ponteiros ao criar membros com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="c2d04-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="c2d04-187">Por exemplo, não há necessidade de passar o índice inicial, porque a aritmética simples de ponteiro pode ser usada para atingir o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="c2d04-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="c2d04-188">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c2d04-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c2d04-189">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c2d04-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d04-190">Veja também</span><span class="sxs-lookup"><span data-stu-id="c2d04-190">See also</span></span>

- [<span data-ttu-id="c2d04-191">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="c2d04-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="c2d04-192">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="c2d04-192">Framework Design Guidelines</span></span>](index.md)
