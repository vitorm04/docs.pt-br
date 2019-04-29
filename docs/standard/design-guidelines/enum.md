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
author: KrzysztofCwalina
ms.openlocfilehash: c0645ba1179c4c6fd961b871b3061cd51174f427
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669089"
---
# <a name="enum-design"></a><span data-ttu-id="77fb8-102">Design de enumeração</span><span class="sxs-lookup"><span data-stu-id="77fb8-102">Enum Design</span></span>
<span data-ttu-id="77fb8-103">Enumerações são um tipo especial de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="77fb8-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="77fb8-104">Há dois tipos de enums: enums de enums e sinalizador simples.</span><span class="sxs-lookup"><span data-stu-id="77fb8-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="77fb8-105">Enums simples representam conjuntos fechados pequeno de opções.</span><span class="sxs-lookup"><span data-stu-id="77fb8-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="77fb8-106">Um exemplo comum de enum simple é um conjunto de cores.</span><span class="sxs-lookup"><span data-stu-id="77fb8-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="77fb8-107">Enums do sinalizador são projetados para dar suporte a operações bit a bit com os valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="77fb8-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="77fb8-108">Um exemplo comum de enumeração de sinalizadores é uma lista de opções.</span><span class="sxs-lookup"><span data-stu-id="77fb8-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="77fb8-109">**✓ DO** usar uma enumeração para fortemente tipados parâmetros, propriedades e retornam valores que representam os conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="77fb8-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="77fb8-110">**✓ DO** favorecer usando um enum em vez de constantes estáticas.</span><span class="sxs-lookup"><span data-stu-id="77fb8-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="77fb8-111">**X DO NOT** usar uma enumeração para abrir conjuntos (como a versão do sistema operacional, os nomes dos seus amigos, etc.).</span><span class="sxs-lookup"><span data-stu-id="77fb8-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="77fb8-112">**X DO NOT** fornecer valores de enum reservado que se destinam para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="77fb8-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="77fb8-113">Você sempre simplesmente pode adicionar valores para o enum existente em um estágio posterior.</span><span class="sxs-lookup"><span data-stu-id="77fb8-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="77fb8-114">Ver [adicionando valores a Enums](#add_value) para obter mais detalhes sobre como adicionar valores a enums.</span><span class="sxs-lookup"><span data-stu-id="77fb8-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="77fb8-115">Valores reservados simplesmente poluam o conjunto de valores reais e tendem a levar a erros de usuário.</span><span class="sxs-lookup"><span data-stu-id="77fb8-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="77fb8-116">**X AVOID** publicamente expondo enums com apenas um valor.</span><span class="sxs-lookup"><span data-stu-id="77fb8-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="77fb8-117">É uma prática comum para garantir a futura extensibilidade das APIs de C adicionar parâmetros reservados a assinaturas de método.</span><span class="sxs-lookup"><span data-stu-id="77fb8-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="77fb8-118">Esses parâmetros reservados podem ser expresso como enums com um valor padrão único.</span><span class="sxs-lookup"><span data-stu-id="77fb8-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="77fb8-119">Isso não deve ser feito em APIs gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="77fb8-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="77fb8-120">Sobrecarga de método permite a adição de parâmetros em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="77fb8-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="77fb8-121">**X DO NOT** incluir valores de sentinela em enums.</span><span class="sxs-lookup"><span data-stu-id="77fb8-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="77fb8-122">Embora, às vezes, eles são úteis para desenvolvedores do framework, os valores de sentinela são confusos para os usuários do framework.</span><span class="sxs-lookup"><span data-stu-id="77fb8-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="77fb8-123">Eles são usados para controlar o estado de enumeração em vez de ser um dos valores do conjunto representado pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="77fb8-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="77fb8-124">**✓ DO** fornecer um valor de zero em enumerações simples.</span><span class="sxs-lookup"><span data-stu-id="77fb8-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="77fb8-125">Considere a possibilidade de chamar o valor de algo como "None".</span><span class="sxs-lookup"><span data-stu-id="77fb8-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="77fb8-126">Se esse valor não for apropriado para essa enum específica, o valor padrão mais comum para o enum deve ser atribuído o valor subjacente de zero.</span><span class="sxs-lookup"><span data-stu-id="77fb8-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="77fb8-127">**✓ CONSIDER** usando <xref:System.Int32> (o padrão na maioria das linguagens de programação) como o tipo subjacente de enum, a menos que qualquer um dos seguintes for verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="77fb8-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
- <span data-ttu-id="77fb8-128">Enum é uma enumeração de sinalizadores e você tiver mais de 32 sinalizadores ou pretende ter mais no futuro.</span><span class="sxs-lookup"><span data-stu-id="77fb8-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
- <span data-ttu-id="77fb8-129">O tipo subjacente deve ser diferente de <xref:System.Int32> mais fáceis de interoperabilidade com código não gerenciado, esperando enums de tamanho diferente.</span><span class="sxs-lookup"><span data-stu-id="77fb8-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
- <span data-ttu-id="77fb8-130">Um tipo subjacente menor poderia resultar em uma economia substancial no espaço.</span><span class="sxs-lookup"><span data-stu-id="77fb8-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="77fb8-131">Se você espera que o enum a ser usado principalmente como um argumento para o fluxo de controle, o tamanho torna pouca diferença.</span><span class="sxs-lookup"><span data-stu-id="77fb8-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="77fb8-132">A economia de tamanho pode ser significativa se:</span><span class="sxs-lookup"><span data-stu-id="77fb8-132">The size savings might be significant if:</span></span>  
  
    - <span data-ttu-id="77fb8-133">Você espera que o enum a ser usado como um campo em uma classe ou estrutura com muita frequência instanciada.</span><span class="sxs-lookup"><span data-stu-id="77fb8-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    - <span data-ttu-id="77fb8-134">Você espera que os usuários criem matrizes grandes ou coleções de enumerar instâncias.</span><span class="sxs-lookup"><span data-stu-id="77fb8-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    - <span data-ttu-id="77fb8-135">Você espera que um grande número de instâncias de enum deve ser serializada.</span><span class="sxs-lookup"><span data-stu-id="77fb8-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="77fb8-136">Para uso na memória, esteja ciente de que os objetos gerenciados são sempre `DWORD`-alinhados, portanto, você precisa efetivamente várias enumerações ou outras estruturas pequenas em uma instância para empacotar um enum menor com para fazer uma diferença, porque o tamanho total de instâncias é sempre vai ser arredondado para um `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="77fb8-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="77fb8-137">**✓ DO** nome do sinalizador enums com substantivos plurais ou frases nominais e simples enums com substantivos singulares ou frases nominais.</span><span class="sxs-lookup"><span data-stu-id="77fb8-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="77fb8-138">**X DO NOT** estender <xref:System.Enum?displayProperty=nameWithType> diretamente.</span><span class="sxs-lookup"><span data-stu-id="77fb8-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="77fb8-139"><xref:System.Enum?displayProperty=nameWithType> é um tipo especial usado pelo CLR para criar enumerações definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="77fb8-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="77fb8-140">A maioria das linguagens de programação fornece um elemento de programação que dá acesso a essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="77fb8-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="77fb8-141">Por exemplo, em c# a `enum` palavra-chave é usada para definir uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="77fb8-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="77fb8-142">Projetando Enums de sinalizador</span><span class="sxs-lookup"><span data-stu-id="77fb8-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="77fb8-143">**✓ DO** se aplicam a <xref:System.FlagsAttribute?displayProperty=nameWithType> para enums de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="77fb8-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="77fb8-144">Não aplique esse atributo para enums simples.</span><span class="sxs-lookup"><span data-stu-id="77fb8-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="77fb8-145">**✓ DO** usar potências de dois para os valores de enumeração de sinalizador, portanto, eles podem ser livremente combinados usando a operação OR bit a bit.</span><span class="sxs-lookup"><span data-stu-id="77fb8-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="77fb8-146">**✓ CONSIDER** fornecer valores de enum especial para comumente usadas combinações de sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="77fb8-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="77fb8-147">Operações bit a bit são um conceito avançado e não devem ser necessárias para tarefas simples.</span><span class="sxs-lookup"><span data-stu-id="77fb8-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="77fb8-148"><xref:System.IO.FileAccess.ReadWrite> é um exemplo de um valor especial.</span><span class="sxs-lookup"><span data-stu-id="77fb8-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="77fb8-149">**X AVOID** criando enums sinalizador onde algumas combinações de valores são inválidas.</span><span class="sxs-lookup"><span data-stu-id="77fb8-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="77fb8-150">**X AVOID** usando o sinalizador valores de enumeração de zero, a menos que o valor representa a "todos os sinalizadores são desmarcados" e é denominado adequadamente, conforme descrito pela seguinte diretriz.</span><span class="sxs-lookup"><span data-stu-id="77fb8-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="77fb8-151">**✓ DO** o nome do valor zero de sinalizador enums `None`.</span><span class="sxs-lookup"><span data-stu-id="77fb8-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="77fb8-152">Para uma enumeração de sinalizador, o valor sempre deve significar "todos os sinalizadores são desmarcados."</span><span class="sxs-lookup"><span data-stu-id="77fb8-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="77fb8-153">Adicionando o valor para Enums</span><span class="sxs-lookup"><span data-stu-id="77fb8-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="77fb8-154">É muito comum para descobrir o que você precisa adicionar valores a uma enum depois que você já tiver enviado ele.</span><span class="sxs-lookup"><span data-stu-id="77fb8-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="77fb8-155">Há um problema potencial de compatibilidade do aplicativo quando o valor recém-adicionado é retornado de uma API existente, porque aplicativos mal escritos não podem manipular o novo valor corretamente.</span><span class="sxs-lookup"><span data-stu-id="77fb8-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="77fb8-156">**✓ CONSIDER** adicionando valores a enums, apesar de um risco de compatibilidade pequeno.</span><span class="sxs-lookup"><span data-stu-id="77fb8-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="77fb8-157">Se você tiver dados reais sobre incompatibilidades de aplicativos causados por adições a uma enum, considere adicionar uma nova API que retorna os valores novos e antigos e substituir a antiga API, o que deve continuar retornando apenas os valores antigos.</span><span class="sxs-lookup"><span data-stu-id="77fb8-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="77fb8-158">Isso garantirá que seus aplicativos existentes permanecem compatíveis.</span><span class="sxs-lookup"><span data-stu-id="77fb8-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="77fb8-159">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="77fb8-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="77fb8-160">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="77fb8-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fb8-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77fb8-161">See also</span></span>

- [<span data-ttu-id="77fb8-162">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="77fb8-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="77fb8-163">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="77fb8-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
