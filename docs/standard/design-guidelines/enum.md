---
title: Design de enumeração
description: Design para enums, que são um tipo especial de tipo de valor. Enums simples mantêm conjuntos pequenos e fechados de opções. Os enums de sinalizador dão suporte a operações de bits em valores de enumeração.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 40a9faf53dc8a03674cd59074244c15cd304bdd2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768531"
---
# <a name="enum-design"></a><span data-ttu-id="2ad74-105">Design de enumeração</span><span class="sxs-lookup"><span data-stu-id="2ad74-105">Enum Design</span></span>

<span data-ttu-id="2ad74-106">Enums são um tipo especial de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2ad74-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="2ad74-107">Há dois tipos de enums: enumerações simples e enums de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="2ad74-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="2ad74-108">Enums simples representam pequenos conjuntos fechados de opções.</span><span class="sxs-lookup"><span data-stu-id="2ad74-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="2ad74-109">Um exemplo comum de enum simples é um conjunto de cores.</span><span class="sxs-lookup"><span data-stu-id="2ad74-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="2ad74-110">Enumerações de sinalizador são projetadas para dar suporte a operações bit a bit nos valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="2ad74-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="2ad74-111">Um exemplo comum de enum Flags é uma lista de opções.</span><span class="sxs-lookup"><span data-stu-id="2ad74-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="2ad74-112">✔️ usar uma enumeração para parâmetros de tipo forte, propriedades e valores de retorno que representam conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="2ad74-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="2ad74-113">✔️ favorecer o uso de uma enumeração em vez de constantes estáticas.</span><span class="sxs-lookup"><span data-stu-id="2ad74-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="2ad74-114">❌Não use um enum para conjuntos abertos (como a versão do sistema operacional, os nomes dos seus amigos, etc.).</span><span class="sxs-lookup"><span data-stu-id="2ad74-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="2ad74-115">❌Não forneça valores de enumeração reservados destinados ao uso futuro.</span><span class="sxs-lookup"><span data-stu-id="2ad74-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="2ad74-116">Você sempre pode simplesmente adicionar valores à enumeração existente em um estágio posterior.</span><span class="sxs-lookup"><span data-stu-id="2ad74-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="2ad74-117">Consulte [Adicionando valores a enums](#add_value) para obter mais detalhes sobre como adicionar valores a enums.</span><span class="sxs-lookup"><span data-stu-id="2ad74-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="2ad74-118">Valores reservados apenas poluim o conjunto de valores reais e tendem a gerar erros do usuário.</span><span class="sxs-lookup"><span data-stu-id="2ad74-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="2ad74-119">❌Evite expor enumerações publicamente com apenas um valor.</span><span class="sxs-lookup"><span data-stu-id="2ad74-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="2ad74-120">Uma prática comum para garantir a futura extensibilidade de APIs C é adicionar parâmetros reservados a assinaturas de método.</span><span class="sxs-lookup"><span data-stu-id="2ad74-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="2ad74-121">Esses parâmetros reservados podem ser expressos como enums com um único valor padrão.</span><span class="sxs-lookup"><span data-stu-id="2ad74-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="2ad74-122">Isso não deve ser feito em APIs gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="2ad74-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="2ad74-123">O método de sobrecarga permite a adição de parâmetros em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="2ad74-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="2ad74-124">❌Não inclua valores de Sentinel em enums.</span><span class="sxs-lookup"><span data-stu-id="2ad74-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="2ad74-125">Embora algumas vezes sejam úteis para os desenvolvedores de estrutura, os valores de sentinela são confusos para os usuários da estrutura.</span><span class="sxs-lookup"><span data-stu-id="2ad74-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="2ad74-126">Eles são usados para rastrear o estado da enumeração em vez de ser um dos valores do conjunto representado pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="2ad74-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="2ad74-127">✔️ fornecer um valor de zero em enums simples.</span><span class="sxs-lookup"><span data-stu-id="2ad74-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="2ad74-128">Considere chamar o valor de algo como "None".</span><span class="sxs-lookup"><span data-stu-id="2ad74-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="2ad74-129">Se esse valor não for apropriado para esse enum específico, o valor padrão mais comum para a enumeração deverá ser atribuído ao valor subjacente zero.</span><span class="sxs-lookup"><span data-stu-id="2ad74-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="2ad74-130">✔️ Considere o uso do <xref:System.Int32> (o padrão na maioria das linguagens de programação) como o tipo subjacente de um enum, a menos que qualquer uma das seguintes opções seja verdadeira:</span><span class="sxs-lookup"><span data-stu-id="2ad74-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="2ad74-131">A enumeração é uma enumeração de sinalizadores e você tem mais de 32 sinalizadores ou espera ter mais no futuro.</span><span class="sxs-lookup"><span data-stu-id="2ad74-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="2ad74-132">O tipo subjacente precisa ser diferente para uma <xref:System.Int32> interoperabilidade mais fácil com código não-gerenciado, esperando diferentes enumerações de tamanho.</span><span class="sxs-lookup"><span data-stu-id="2ad74-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="2ad74-133">Um tipo subjacente menor resultaria em uma economia significativa no espaço.</span><span class="sxs-lookup"><span data-stu-id="2ad74-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="2ad74-134">Se você espera que a enumeração seja usada principalmente como um argumento para o fluxo de controle, o tamanho faz pouca diferença.</span><span class="sxs-lookup"><span data-stu-id="2ad74-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="2ad74-135">A economia de tamanho pode ser significativa se:</span><span class="sxs-lookup"><span data-stu-id="2ad74-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="2ad74-136">Você espera que a enumeração seja usada como um campo em uma estrutura ou classe instanciada com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="2ad74-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="2ad74-137">Você espera que os usuários criem grandes matrizes ou coleções das instâncias de enumeração.</span><span class="sxs-lookup"><span data-stu-id="2ad74-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="2ad74-138">Você espera que um grande número de instâncias da enumeração seja serializado.</span><span class="sxs-lookup"><span data-stu-id="2ad74-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="2ad74-139">Para uso na memória, lembre-se de que os objetos gerenciados são sempre `DWORD` alinhados, de modo que você precisa efetivamente de várias enumerações ou outras pequenas estruturas em uma instância para empacotar uma enumeração menor com a fim de fazer uma diferença, pois o tamanho total da instância sempre será arredondado para um `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="2ad74-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="2ad74-140">✔️ as enumerações de sinalizador de nome com substantivos plural ou frases de substantivo e enums simples com substantivos ou frases de substantivo singulares.</span><span class="sxs-lookup"><span data-stu-id="2ad74-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="2ad74-141">❌Não estenda <xref:System.Enum?displayProperty=nameWithType> diretamente.</span><span class="sxs-lookup"><span data-stu-id="2ad74-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="2ad74-142"><xref:System.Enum?displayProperty=nameWithType>é um tipo especial usado pelo CLR para criar enumerações definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2ad74-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="2ad74-143">A maioria das linguagens de programação fornece um elemento de programação que oferece acesso a essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="2ad74-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="2ad74-144">Por exemplo, em C#, a `enum` palavra-chave é usada para definir uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="2ad74-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="2ad74-145">Criando enums de sinalizador</span><span class="sxs-lookup"><span data-stu-id="2ad74-145">Designing Flag Enums</span></span>

<span data-ttu-id="2ad74-146">✔️ aplicar as <xref:System.FlagsAttribute?displayProperty=nameWithType> enumerações de sinalizador to.</span><span class="sxs-lookup"><span data-stu-id="2ad74-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="2ad74-147">Não aplique esse atributo a enums simples.</span><span class="sxs-lookup"><span data-stu-id="2ad74-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="2ad74-148">✔️ usar potências de dois para os valores de enumeração de sinalizador para que eles possam ser livremente combinados usando a operação or</span><span class="sxs-lookup"><span data-stu-id="2ad74-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="2ad74-149">✔️ Considere fornecer valores de enumeração especiais para combinações de sinalizadores comumente usados.</span><span class="sxs-lookup"><span data-stu-id="2ad74-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="2ad74-150">As operações de bit a bit são um conceito avançado e não devem ser necessárias para tarefas simples.</span><span class="sxs-lookup"><span data-stu-id="2ad74-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="2ad74-151"><xref:System.IO.FileAccess.ReadWrite>é um exemplo de tal valor especial.</span><span class="sxs-lookup"><span data-stu-id="2ad74-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="2ad74-152">❌Evite criar enums de sinalizador em que determinadas combinações de valores são inválidas.</span><span class="sxs-lookup"><span data-stu-id="2ad74-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="2ad74-153">❌Evite usar os valores de enumeração de sinalizador zero, a menos que o valor represente "todos os sinalizadores sejam limpos" e seja nomeado adequadamente, conforme prescrito pela próxima diretriz.</span><span class="sxs-lookup"><span data-stu-id="2ad74-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="2ad74-154">✔️ nomear o valor zero de enumerações de sinalizador `None` .</span><span class="sxs-lookup"><span data-stu-id="2ad74-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="2ad74-155">Para uma enumeração de sinalizador, o valor sempre deve significar "todos os sinalizadores são limpos".</span><span class="sxs-lookup"><span data-stu-id="2ad74-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="2ad74-156">Adicionando valor a enums</span><span class="sxs-lookup"><span data-stu-id="2ad74-156">Adding Value to Enums</span></span>

<span data-ttu-id="2ad74-157">É muito comum descobrir que você precisa adicionar valores a uma enumeração depois que você já o enviou.</span><span class="sxs-lookup"><span data-stu-id="2ad74-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="2ad74-158">Há um problema potencial de compatibilidade de aplicativo quando o valor recém-adicionado é retornado de uma API existente, pois aplicativos mal escritos podem não lidar corretamente com o novo valor.</span><span class="sxs-lookup"><span data-stu-id="2ad74-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="2ad74-159">✔️ CONSIDERAR a adição de valores a enums, apesar de um pequeno risco de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2ad74-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="2ad74-160">Se você tiver dados reais sobre incompatibilidades de aplicativos causadas por adições a uma enumeração, considere adicionar uma nova API que retorne os valores novos e antigos e substitua a antiga API, que deve continuar retornando apenas os valores antigos.</span><span class="sxs-lookup"><span data-stu-id="2ad74-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="2ad74-161">Isso garantirá que seus aplicativos existentes permaneçam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="2ad74-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="2ad74-162">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2ad74-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="2ad74-163">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2ad74-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2ad74-164">Veja também</span><span class="sxs-lookup"><span data-stu-id="2ad74-164">See also</span></span>

- [<span data-ttu-id="2ad74-165">Diretrizes de design de tipo</span><span class="sxs-lookup"><span data-stu-id="2ad74-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="2ad74-166">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="2ad74-166">Framework Design Guidelines</span></span>](index.md)
