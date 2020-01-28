---
title: Design de enumeração
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 3b24bfefd3edb0585e9c6369e9b8151b17151661
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741705"
---
# <a name="enum-design"></a><span data-ttu-id="396d2-102">Design de enumeração</span><span class="sxs-lookup"><span data-stu-id="396d2-102">Enum Design</span></span>

<span data-ttu-id="396d2-103">Enums são um tipo especial de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="396d2-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="396d2-104">Há dois tipos de enums: enumerações simples e enums de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="396d2-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="396d2-105">Enums simples representam pequenos conjuntos fechados de opções.</span><span class="sxs-lookup"><span data-stu-id="396d2-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="396d2-106">Um exemplo comum de enum simples é um conjunto de cores.</span><span class="sxs-lookup"><span data-stu-id="396d2-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="396d2-107">Enumerações de sinalizador são projetadas para dar suporte a operações bit a bit nos valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="396d2-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="396d2-108">Um exemplo comum de enum Flags é uma lista de opções.</span><span class="sxs-lookup"><span data-stu-id="396d2-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="396d2-109">✔️ usar uma enumeração para parâmetros de tipo forte, propriedades e valores de retorno que representam conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="396d2-109">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="396d2-110">✔️ favorecer o uso de uma enumeração em vez de constantes estáticas.</span><span class="sxs-lookup"><span data-stu-id="396d2-110">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="396d2-111">❌ não use um enum para conjuntos abertos (como a versão do sistema operacional, os nomes dos seus amigos, etc.).</span><span class="sxs-lookup"><span data-stu-id="396d2-111">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="396d2-112">❌ não fornecem valores de enumeração reservados destinados a uso futuro.</span><span class="sxs-lookup"><span data-stu-id="396d2-112">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="396d2-113">Você sempre pode simplesmente adicionar valores à enumeração existente em um estágio posterior.</span><span class="sxs-lookup"><span data-stu-id="396d2-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="396d2-114">Consulte [Adicionando valores a enums](#add_value) para obter mais detalhes sobre como adicionar valores a enums.</span><span class="sxs-lookup"><span data-stu-id="396d2-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="396d2-115">Valores reservados apenas poluim o conjunto de valores reais e tendem a gerar erros do usuário.</span><span class="sxs-lookup"><span data-stu-id="396d2-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="396d2-116">❌ evitar a exposição pública de enumerações com apenas um valor.</span><span class="sxs-lookup"><span data-stu-id="396d2-116">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="396d2-117">Uma prática comum para garantir a futura extensibilidade de APIs C é adicionar parâmetros reservados a assinaturas de método.</span><span class="sxs-lookup"><span data-stu-id="396d2-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="396d2-118">Esses parâmetros reservados podem ser expressos como enums com um único valor padrão.</span><span class="sxs-lookup"><span data-stu-id="396d2-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="396d2-119">Isso não deve ser feito em APIs gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="396d2-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="396d2-120">O método de sobrecarga permite a adição de parâmetros em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="396d2-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="396d2-121">❌ não incluem valores de Sentinel em enums.</span><span class="sxs-lookup"><span data-stu-id="396d2-121">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="396d2-122">Embora algumas vezes sejam úteis para os desenvolvedores de estrutura, os valores de sentinela são confusos para os usuários da estrutura.</span><span class="sxs-lookup"><span data-stu-id="396d2-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="396d2-123">Eles são usados para rastrear o estado da enumeração em vez de ser um dos valores do conjunto representado pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="396d2-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="396d2-124">✔️ fornecer um valor de zero em enums simples.</span><span class="sxs-lookup"><span data-stu-id="396d2-124">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="396d2-125">Considere chamar o valor de algo como "None".</span><span class="sxs-lookup"><span data-stu-id="396d2-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="396d2-126">Se esse valor não for apropriado para esse enum específico, o valor padrão mais comum para a enumeração deverá ser atribuído ao valor subjacente zero.</span><span class="sxs-lookup"><span data-stu-id="396d2-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="396d2-127">✔️ Considere o uso de <xref:System.Int32> (o padrão na maioria das linguagens de programação) como o tipo subjacente de um enum, a menos que qualquer uma das seguintes opções seja verdadeira:</span><span class="sxs-lookup"><span data-stu-id="396d2-127">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="396d2-128">A enumeração é uma enumeração de sinalizadores e você tem mais de 32 sinalizadores ou espera ter mais no futuro.</span><span class="sxs-lookup"><span data-stu-id="396d2-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="396d2-129">O tipo subjacente precisa ser diferente de <xref:System.Int32> para interoperabilidade mais fácil com código não gerenciado esperando diferentes enumerações de tamanho.</span><span class="sxs-lookup"><span data-stu-id="396d2-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="396d2-130">Um tipo subjacente menor resultaria em uma economia significativa no espaço.</span><span class="sxs-lookup"><span data-stu-id="396d2-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="396d2-131">Se você espera que a enumeração seja usada principalmente como um argumento para o fluxo de controle, o tamanho faz pouca diferença.</span><span class="sxs-lookup"><span data-stu-id="396d2-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="396d2-132">A economia de tamanho pode ser significativa se:</span><span class="sxs-lookup"><span data-stu-id="396d2-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="396d2-133">Você espera que a enumeração seja usada como um campo em uma estrutura ou classe instanciada com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="396d2-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="396d2-134">Você espera que os usuários criem grandes matrizes ou coleções das instâncias de enumeração.</span><span class="sxs-lookup"><span data-stu-id="396d2-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="396d2-135">Você espera que um grande número de instâncias da enumeração seja serializado.</span><span class="sxs-lookup"><span data-stu-id="396d2-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="396d2-136">Para uso na memória, lembre-se de que os objetos gerenciados são sempre alinhados `DWORD`, de modo que você precisa efetivamente de várias enumerações ou outras pequenas estruturas em uma instância para empacotar uma enumeração menor com o para fazer uma diferença, pois o tamanho total da instância sempre será arredondado para um `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="396d2-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="396d2-137">✔️ as enumerações de sinalizador de nome com substantivos plural ou frases de substantivo e enums simples com substantivos ou frases de substantivo singulares.</span><span class="sxs-lookup"><span data-stu-id="396d2-137">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="396d2-138">❌ não estender <xref:System.Enum?displayProperty=nameWithType> diretamente.</span><span class="sxs-lookup"><span data-stu-id="396d2-138">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="396d2-139"><xref:System.Enum?displayProperty=nameWithType> é um tipo especial usado pelo CLR para criar enumerações definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="396d2-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="396d2-140">A maioria das linguagens de programação fornece um elemento de programação que oferece acesso a essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="396d2-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="396d2-141">Por exemplo, na C# palavra-chave `enum` é usada para definir uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="396d2-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="396d2-142">Criando enums de sinalizador</span><span class="sxs-lookup"><span data-stu-id="396d2-142">Designing Flag Enums</span></span>

<span data-ttu-id="396d2-143">✔️ aplicar a <xref:System.FlagsAttribute?displayProperty=nameWithType> para sinalizar enums.</span><span class="sxs-lookup"><span data-stu-id="396d2-143">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="396d2-144">Não aplique esse atributo a enums simples.</span><span class="sxs-lookup"><span data-stu-id="396d2-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="396d2-145">✔️ usar potências de dois para os valores de enumeração de sinalizador para que eles possam ser livremente combinados usando a operação or</span><span class="sxs-lookup"><span data-stu-id="396d2-145">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="396d2-146">✔️ Considere fornecer valores de enumeração especiais para combinações de sinalizadores comumente usados.</span><span class="sxs-lookup"><span data-stu-id="396d2-146">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="396d2-147">As operações de bit a bit são um conceito avançado e não devem ser necessárias para tarefas simples.</span><span class="sxs-lookup"><span data-stu-id="396d2-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="396d2-148"><xref:System.IO.FileAccess.ReadWrite> é um exemplo desse valor especial.</span><span class="sxs-lookup"><span data-stu-id="396d2-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="396d2-149">❌ evitar a criação de enums de sinalizador em que determinadas combinações de valores são inválidas.</span><span class="sxs-lookup"><span data-stu-id="396d2-149">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="396d2-150">❌ Evite usar os valores de enumeração de sinalizador igual a zero, a menos que o valor represente "todos os sinalizadores sejam limpos" e seja nomeado adequadamente, conforme prescrito pela próxima diretriz.</span><span class="sxs-lookup"><span data-stu-id="396d2-150">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="396d2-151">✔️ nomear o valor zero de enumerações de sinalizador `None`.</span><span class="sxs-lookup"><span data-stu-id="396d2-151">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="396d2-152">Para uma enumeração de sinalizador, o valor sempre deve significar "todos os sinalizadores são limpos".</span><span class="sxs-lookup"><span data-stu-id="396d2-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="396d2-153">Adicionando valor a enums</span><span class="sxs-lookup"><span data-stu-id="396d2-153">Adding Value to Enums</span></span>

<span data-ttu-id="396d2-154">É muito comum descobrir que você precisa adicionar valores a uma enumeração depois que você já o enviou.</span><span class="sxs-lookup"><span data-stu-id="396d2-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="396d2-155">Há um problema potencial de compatibilidade de aplicativo quando o valor recém-adicionado é retornado de uma API existente, pois aplicativos mal escritos podem não lidar corretamente com o novo valor.</span><span class="sxs-lookup"><span data-stu-id="396d2-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="396d2-156">✔️ CONSIDERAR a adição de valores a enums, apesar de um pequeno risco de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="396d2-156">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="396d2-157">Se você tiver dados reais sobre incompatibilidades de aplicativos causadas por adições a uma enumeração, considere adicionar uma nova API que retorne os valores novos e antigos e substitua a antiga API, que deve continuar retornando apenas os valores antigos.</span><span class="sxs-lookup"><span data-stu-id="396d2-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="396d2-158">Isso garantirá que seus aplicativos existentes permaneçam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="396d2-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="396d2-159">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="396d2-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="396d2-160">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="396d2-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="396d2-161">Veja também</span><span class="sxs-lookup"><span data-stu-id="396d2-161">See also</span></span>

- [<span data-ttu-id="396d2-162">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="396d2-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="396d2-163">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="396d2-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
