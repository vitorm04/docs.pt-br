---
title: Avaliar alterações da falha – .NET Core
description: Saiba mais sobre as maneiras como o .NET Core tenta manter a compatibilidade para desenvolvedores em versões do .NET.
ms.date: 06/10/2019
ms.openlocfilehash: 4c3f051bf37ea4753d916ee22fedf97a9bad5892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089343"
---
# <a name="evaluate-breaking-changes-in-net-core"></a><span data-ttu-id="ab32f-103">Avaliar alterações da falha no .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab32f-103">Evaluate breaking changes in .NET Core</span></span>

<span data-ttu-id="ab32f-104">Ao longo de sua história, o .NET tentou manter um alto nível de compatibilidade de versão para versão e em todos os tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="ab32f-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="ab32f-105">Isso também ocorre no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab32f-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="ab32f-106">Embora o .NET Core possa ser considerado uma nova tecnologia independente do .NET Framework, dois fatores principais limitam a capacidade do .NET Core de divergir do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ab32f-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="ab32f-107">Um grande número de desenvolvedores originalmente desenvolveu ou continua a desenvolver aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab32f-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="ab32f-108">Eles esperam um comportamento consistente nas implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="ab32f-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="ab32f-109">Os projetos da biblioteca .NET Standard permitem que os desenvolvedores criem bibliotecas voltadas a APIs comuns compartilhadas pelo .NET Core e pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab32f-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="ab32f-110">Os desenvolvedores esperam que uma biblioteca usada em um aplicativo .NET Core se comporte de maneira idêntica à mesma biblioteca usada em um aplicativo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab32f-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="ab32f-111">Além da compatibilidade entre as implementações do .NET, os desenvolvedores esperam um alto nível de compatibilidade nas versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab32f-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="ab32f-112">Em particular, o código escrito para uma versão anterior do .NET Core precisam ser executado sem problemas em uma versão posterior do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab32f-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="ab32f-113">Na verdade, muitos desenvolvedores esperam que as novas APIs encontradas em versões recém-lançadas do .NET Core também sejam compatíveis com as versões de pré-lançamento em que essas APIs foram apresentadas.</span><span class="sxs-lookup"><span data-stu-id="ab32f-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="ab32f-114">Este artigo descreve as categorias de alterações de compatibilidade (ou alterações significativas) e a maneira como a equipe do .NET avalia alterações em cada uma dessas categorias.</span><span class="sxs-lookup"><span data-stu-id="ab32f-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="ab32f-115">Compreender como a equipe do .NET aborda as possíveis alterações de falha é particularmente útil para os desenvolvedores que abrem solicitações de pull no repositório [dotnet/corefx](https://github.com/dotnet/corefx) do GitHub que modificam o comportamento das APIs existentes.</span><span class="sxs-lookup"><span data-stu-id="ab32f-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who are opening pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="ab32f-116">Para obter uma definição das categorias de compatibilidade, como compatibilidade binária e compatibilidade com versões anteriores, confira [Categorias de alterações significativas](categories.md).</span><span class="sxs-lookup"><span data-stu-id="ab32f-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="ab32f-117">As seções a seguir descrevem as categorias de alterações feitas nas APIs do .NET Core e o impacto delas na compatibilidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab32f-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="ab32f-118">O ícone de ✔️ indica que um determinado tipo de alteração é permitido, ❌ indica que ele não é permitido e ❓ indica uma alteração que pode ou não ser permitida.</span><span class="sxs-lookup"><span data-stu-id="ab32f-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="ab32f-119">Alterações nessa última categoria exigem uma avaliação do quanto o comportamento anterior era previsível, óbvio e consistente.</span><span class="sxs-lookup"><span data-stu-id="ab32f-119">Changes in this last category require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="ab32f-120">Além de servir como um guia de como as alterações nas bibliotecas .NET Core são avaliadas, os desenvolvedores de bibliotecas também podem usar esses critérios para avaliar as alterações em suas bibliotecas voltadas a várias implementações e versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="ab32f-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="ab32f-121">Modificações no contrato público</span><span class="sxs-lookup"><span data-stu-id="ab32f-121">Modifications to the public contract</span></span>

<span data-ttu-id="ab32f-122">Alterações nesta categoria *modificam* a área de superfície pública de um tipo.</span><span class="sxs-lookup"><span data-stu-id="ab32f-122">Changes in this category *modify* the public surface area of a type.</span></span> <span data-ttu-id="ab32f-123">A maioria das alterações nesta categoria não é permitida porque viola a *compatibilidade com versões anteriores* (a capacidade de um aplicativo desenvolvido com a versão anterior de uma API ser executado sem recompilação em uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="ab32f-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="ab32f-124">Tipos</span><span class="sxs-lookup"><span data-stu-id="ab32f-124">Types</span></span>

- <span data-ttu-id="ab32f-125">**✔️ Remover uma implementação de interface de um tipo quando a interface já foi implementada por um tipo base**</span><span class="sxs-lookup"><span data-stu-id="ab32f-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="ab32f-126">**❓ Adicionar uma nova implementação de interface a um tipo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="ab32f-127">Essa é uma alteração aceitável, pois não afeta negativamente os clientes existentes.</span><span class="sxs-lookup"><span data-stu-id="ab32f-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="ab32f-128">Quaisquer alterações no tipo precisam funcionar dentro dos limites das alterações aceitáveis ​​definidas aqui para que a nova implementação permaneça aceitável.</span><span class="sxs-lookup"><span data-stu-id="ab32f-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="ab32f-129">É necessário ter um extremo cuidado ao adicionar interfaces que afetam diretamente a capacidade de um designer ou serializador de gerar código ou dados que não podem ser consumidos em um nível anterior.</span><span class="sxs-lookup"><span data-stu-id="ab32f-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="ab32f-130">Um exemplo é a interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="ab32f-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="ab32f-131">**❓ Introduzir uma nova classe base**</span><span class="sxs-lookup"><span data-stu-id="ab32f-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="ab32f-132">Um tipo poderá ser introduzido em uma hierarquia entre dois tipos existentes se ele não introduzir novos membros [abstratos](../../csharp/language-reference/keywords/abstract.md)ou alterar a semântica ou o comportamento de tipos existentes.</span><span class="sxs-lookup"><span data-stu-id="ab32f-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="ab32f-133">Por exemplo, no .NET Framework 2.0, a classe <xref:System.Data.Common.DbConnection> tornou-se uma nova classe base para <xref:System.Data.SqlClient.SqlConnection>, que antes era derivada diretamente de <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="ab32f-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="ab32f-134">**✔️ Mover um tipo de um assembly para outro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="ab32f-135">O assembly *antigo* precisa ser marcado com o <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> que aponta para o novo assembly.</span><span class="sxs-lookup"><span data-stu-id="ab32f-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="ab32f-136">**✔️ Alterar um tipo de [struct](../../csharp/language-reference/keywords/struct.md) para um tipo `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="ab32f-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="ab32f-137">A alteração de um tipo `readonly struct` para um tipo `struct` não é permitida.</span><span class="sxs-lookup"><span data-stu-id="ab32f-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>
  
- <span data-ttu-id="ab32f-138">**✔️ Adicionar a palavra-chave [sealed](../../csharp/language-reference/keywords/sealed.md) ou [abstract](../../csharp/language-reference/keywords/abstract.md) a um tipo quando não há construtores *accessíveis* (públicos ou protegidos)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="ab32f-139">**✔️ Expandir a visibilidade de um tipo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="ab32f-140">**❌ alterar o namespace ou o nome de um tipo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="ab32f-141">**❌ renomear ou remover um tipo público**</span><span class="sxs-lookup"><span data-stu-id="ab32f-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="ab32f-142">Isso interrompe todo o código que usa o tipo renomeado ou removido.</span><span class="sxs-lookup"><span data-stu-id="ab32f-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="ab32f-143">**❌ alterar o tipo subjacente de uma enumeração**</span><span class="sxs-lookup"><span data-stu-id="ab32f-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="ab32f-144">Esta é uma alteração significativa de tempo de compilação e comportamental, bem como uma alteração significativa binária que pode tornar os argumentos de atributo inseparáveis.</span><span class="sxs-lookup"><span data-stu-id="ab32f-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="ab32f-145">**❌ selando um tipo que não foi lacrado anteriormente**</span><span class="sxs-lookup"><span data-stu-id="ab32f-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="ab32f-146">**❌ adicionar uma interface ao conjunto de tipos de base de uma interface**</span><span class="sxs-lookup"><span data-stu-id="ab32f-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="ab32f-147">Se uma interface implementar uma interface não implementada anteriormente, todos os tipos que implementaram a versão original da interface serão corrompidos.</span><span class="sxs-lookup"><span data-stu-id="ab32f-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="ab32f-148">**❓ Remover uma classe do conjunto de classes base ou uma interface do conjunto de interfaces implementadas**</span><span class="sxs-lookup"><span data-stu-id="ab32f-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="ab32f-149">Há uma exceção à regra para remoção de interface: é possível adicionar a implementação de uma interface derivada da interface removida.</span><span class="sxs-lookup"><span data-stu-id="ab32f-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="ab32f-150">Por exemplo, você pode remover <xref:System.IDisposable> se o tipo ou interface agora implementa <xref:System.ComponentModel.IComponent>, que implementa <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="ab32f-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="ab32f-151">**❌ alterar um tipo de `readonly struct` para um tipo de [struct](../../csharp/language-reference/keywords/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="ab32f-152">A alteração de um tipo `struct` para um tipo `readonly struct` é permitida.</span><span class="sxs-lookup"><span data-stu-id="ab32f-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="ab32f-153">**❌ alterar um tipo de [struct](../../csharp/language-reference/keywords/struct.md) para um tipo `ref struct`, e vice-versa**</span><span class="sxs-lookup"><span data-stu-id="ab32f-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="ab32f-154">**❌ reduzir a visibilidade de um tipo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="ab32f-155">No entanto, aumentar a visibilidade de um tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="ab32f-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="ab32f-156">Membros</span><span class="sxs-lookup"><span data-stu-id="ab32f-156">Members</span></span>

- <span data-ttu-id="ab32f-157">**✔️ Expandir a visibilidade de um membro que não é [virtual](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="ab32f-158">**✔️ Adicionar um membro abstrato a um tipo público que não tenha construtores *acessíveis* (públicos ou protegidos) ou a um tipo que seja [sealed](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="ab32f-159">No entanto, adicionar um membro abstrato a um tipo que tenha construtores acessíveis (públicos ou protegidos) e não seja `sealed` não é permitido.</span><span class="sxs-lookup"><span data-stu-id="ab32f-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="ab32f-160">**✔️ Restringir a visibilidade de um membro [protegido](../../csharp/language-reference/keywords/protected.md) quando o tipo não tem construtores acessíveis (públicos ou protegidos) ou o tipo é [sealed](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="ab32f-161">**✔️ Mover um membro para uma classe superior ao tipo do qual ele foi removido na hierarquia**</span><span class="sxs-lookup"><span data-stu-id="ab32f-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="ab32f-162">**✔️ Adicionar ou remover uma substituição**</span><span class="sxs-lookup"><span data-stu-id="ab32f-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="ab32f-163">A introdução de uma substituição pode fazer com que os consumidores anteriores pulem a substituição ao chamar a [base](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="ab32f-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="ab32f-164">**✔ Adicionar um construtor a uma classe, junto com um construtor padrão (sem parâmetros) se a classe anteriormente não tinha construtores**</span><span class="sxs-lookup"><span data-stu-id="ab32f-164">**✔️ Adding a constructor to a class, along with a default (parameterless) constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="ab32f-165">No entanto, não é permitido adicionar um construtor a uma classe que anteriormente não tinha construtores *sem* adicionar o construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ab32f-165">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="ab32f-166">**✔️ Alterar um membro de [abstract](../../csharp/language-reference/keywords/abstract.md) para [virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="ab32f-167">**✔️ Alterar de `ref readonly` para um valor retornado `ref` (exceto para interfaces ou métodos virtuais)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="ab32f-168">**✔️ Remover [readonly](../../csharp/language-reference/keywords/readonly.md) de um campo, a menos que o tipo estático do campo seja um tipo de valor mutável**</span><span class="sxs-lookup"><span data-stu-id="ab32f-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="ab32f-169">**✔️ Chamar um novo evento que não foi definido anteriormente**</span><span class="sxs-lookup"><span data-stu-id="ab32f-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="ab32f-170">**❓ Adicionar um novo campo de instância a um tipo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="ab32f-171">Essa alteração afeta a serialização.</span><span class="sxs-lookup"><span data-stu-id="ab32f-171">This change impacts serialization.</span></span>

- <span data-ttu-id="ab32f-172">**❌ renomear ou remover um membro público ou parâmetro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="ab32f-173">Isso interrompe todo o código que usa o membro ou parâmetro renomeado ou removido.</span><span class="sxs-lookup"><span data-stu-id="ab32f-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="ab32f-174">Isso inclui remover ou renomear um getter ou setter de uma propriedade, bem como renomear ou remover membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ab32f-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="ab32f-175">**❌ adicionar um membro a uma interface**</span><span class="sxs-lookup"><span data-stu-id="ab32f-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="ab32f-176">**❌ alterar o valor de uma constante pública ou membro de enumeração**</span><span class="sxs-lookup"><span data-stu-id="ab32f-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="ab32f-177">**❌ alterar o tipo de uma propriedade, campo, parâmetro ou valor de retorno**</span><span class="sxs-lookup"><span data-stu-id="ab32f-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="ab32f-178">**❌ adicionar, remover ou alterar a ordem dos parâmetros**</span><span class="sxs-lookup"><span data-stu-id="ab32f-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="ab32f-179">**❌ adicionar ou remover a palavra-chave [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) ou [ref](../../csharp/language-reference/keywords/ref.md) de um parâmetro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="ab32f-180">**❌ renomear um parâmetro (incluindo a alteração de seu caso)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="ab32f-181">Isso é considerado significativo por dois motivos:</span><span class="sxs-lookup"><span data-stu-id="ab32f-181">This is considered breaking for two reasons:</span></span>
  
  - <span data-ttu-id="ab32f-182">Interrompe cenários de associação tardia, como o recurso de associação tardia no Visual Basic e [dinâmico](../../csharp/language-reference/keywords/dynamic.md) no C#.</span><span class="sxs-lookup"><span data-stu-id="ab32f-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/keywords/dynamic.md) in C#.</span></span>
  
  - <span data-ttu-id="ab32f-183">Interrompe a [compatibilidade de origem](categories.md#source-compatibility) quando os desenvolvedores usam [argumentos nomeados](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="ab32f-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="ab32f-184">**❌ alterar de um valor de retorno de `ref` para um valor de retorno `ref readonly`**</span><span class="sxs-lookup"><span data-stu-id="ab32f-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="ab32f-185">**❌️ alteração de um `ref readonly` para um valor de retorno de `ref` em um método ou interface virtual**</span><span class="sxs-lookup"><span data-stu-id="ab32f-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="ab32f-186">**❌ adicionar ou remover [abstrato](../../csharp/language-reference/keywords/abstract.md) de um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="ab32f-187">**❌ remover a palavra-chave [virtual](../../csharp/language-reference/keywords/virtual.md) de um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="ab32f-188">Embora isso geralmente não seja uma alteração significativa, pois o compilador C# tende a emitir instruções [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) de IL (Intermediate Language) para chamar métodos não virtuais (`callvirt` executa uma verificação nula, enquanto uma chamada normal não), esse comportamento não é invariável por vários motivos:</span><span class="sxs-lookup"><span data-stu-id="ab32f-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="ab32f-189">C# não é a única linguagem de destino do .NET.</span><span class="sxs-lookup"><span data-stu-id="ab32f-189">C# is not the only language that .NET targets.</span></span>
  
  - <span data-ttu-id="ab32f-190">O compilador C# tenta otimizar cada vez mais `callvirt` a uma chamada normal sempre que o método de destino é não virtual e provavelmente não é nulo (como um método acessado por meio de operador de propagação nula [?.](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="ab32f-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>
  
  <span data-ttu-id="ab32f-191">Tornar um método virtual significa que o código do consumidor em geral acabaria chamando-o não virtualmente.</span><span class="sxs-lookup"><span data-stu-id="ab32f-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="ab32f-192">**❌ adicionar a palavra-chave [virtual](../../csharp/language-reference/keywords/virtual.md) a um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="ab32f-193">**❌ tornar um membro Virtual abstrato**</span><span class="sxs-lookup"><span data-stu-id="ab32f-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="ab32f-194">Um [membro virtual](../../csharp/language-reference/keywords/virtual.md) fornece uma implementação de método que *pode ser* substituída por uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="ab32f-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="ab32f-195">Um [membro abstrato](../../csharp/language-reference/keywords/abstract.md) não fornece nenhuma implementação e *precisa ser* substituído.</span><span class="sxs-lookup"><span data-stu-id="ab32f-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="ab32f-196">**❌ adicionar um membro abstrato a um tipo público que tem construtores acessíveis (públicos ou protegidos) e que não está [lacrado](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="ab32f-197">**❌ adicionar ou remover a palavra-chave [estática](../../csharp/language-reference/keywords/static.md) de um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="ab32f-198">**❌ adicionar uma sobrecarga que impede uma sobrecarga existente e define um comportamento diferente**</span><span class="sxs-lookup"><span data-stu-id="ab32f-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="ab32f-199">Isso interrompe os clientes existentes que estavam vinculados à sobrecarga anterior.</span><span class="sxs-lookup"><span data-stu-id="ab32f-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="ab32f-200">Por exemplo, se uma classe tiver uma única versão de um método que aceite um <xref:System.UInt32>, um consumidor existente será vinculado a essa sobrecarga ao passar um valor <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="ab32f-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="ab32f-201">No entanto, se você adicionar uma sobrecarga que aceita um <xref:System.Int32>, ao recompilar ou usar associação tardia, o compilador agora se associa à nova sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="ab32f-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="ab32f-202">Se resultar em um comportamento diferente, significa que essa é uma alteração significativa.</span><span class="sxs-lookup"><span data-stu-id="ab32f-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="ab32f-203">**❌ adicionar um construtor a uma classe que anteriormente não tinha nenhum construtor sem adicionar o construtor de parâmetros**</span><span class="sxs-lookup"><span data-stu-id="ab32f-203">**❌ Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="ab32f-204">**❌️ adicionar [ReadOnly](../../csharp/language-reference/keywords/readonly.md) a um campo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="ab32f-205">**❌ reduzir a visibilidade de um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="ab32f-206">Isso inclui restringir a visibilidade de um membro [protegido](../../csharp/language-reference/keywords/protected.md) quando o tipo não tem construtores *acessíveis* (públicos ou protegidos) e o tipo *não* é [sealed](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="ab32f-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="ab32f-207">Se esse não for o caso, será permitido reduzir a visibilidade de um membro protegido.</span><span class="sxs-lookup"><span data-stu-id="ab32f-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="ab32f-208">Aumentar a visibilidade de um tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="ab32f-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="ab32f-209">**❌ alterar o tipo de um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="ab32f-210">Não é possível modificar o valor de retorno de um método ou o tipo de uma propriedade ou campo.</span><span class="sxs-lookup"><span data-stu-id="ab32f-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="ab32f-211">Por exemplo, a assinatura de um método que retorna um <xref:System.Object> não pode ser alterada para retornar um <xref:System.String> ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="ab32f-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="ab32f-212">**❌ adicionar um campo a uma struct que anteriormente não tinha nenhum estado**</span><span class="sxs-lookup"><span data-stu-id="ab32f-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="ab32f-213">As regras de atribuição definidas permitem o uso de variáveis ​​não inicializadas, desde que o tipo de variável seja um struct sem estado.</span><span class="sxs-lookup"><span data-stu-id="ab32f-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="ab32f-214">Se o struct for alterado para “com estado”, o código poderá acabar com dados não inicializados.</span><span class="sxs-lookup"><span data-stu-id="ab32f-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="ab32f-215">Isso é potencialmente uma interrupção de fonte e uma alteração binária significativa.</span><span class="sxs-lookup"><span data-stu-id="ab32f-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="ab32f-216">**❌ acionar um evento existente quando ele nunca foi acionado antes**</span><span class="sxs-lookup"><span data-stu-id="ab32f-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="ab32f-217">Alterações comportamentais</span><span class="sxs-lookup"><span data-stu-id="ab32f-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="ab32f-218">Assemblies</span><span class="sxs-lookup"><span data-stu-id="ab32f-218">Assemblies</span></span>

- <span data-ttu-id="ab32f-219">**✔️ Tornar um assembly portátil quando ainda há suporte para as mesmas plataformas**</span><span class="sxs-lookup"><span data-stu-id="ab32f-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="ab32f-220">**❌ alterar o nome de um assembly**</span><span class="sxs-lookup"><span data-stu-id="ab32f-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="ab32f-221">**❌ alterar a chave pública de um assembly**</span><span class="sxs-lookup"><span data-stu-id="ab32f-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="ab32f-222">Propriedades, campos, parâmetros e valores retornados</span><span class="sxs-lookup"><span data-stu-id="ab32f-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="ab32f-223">**✔️ Alterar o valor de uma propriedade, campo, valor retornado ou parâmetro [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) para um tipo mais derivado**</span><span class="sxs-lookup"><span data-stu-id="ab32f-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="ab32f-224">Por exemplo, um método que retorna um tipo de <xref:System.Object> pode retornar uma instância <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab32f-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="ab32f-225">(No entanto, a assinatura do método não pode ser alterada.)</span><span class="sxs-lookup"><span data-stu-id="ab32f-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="ab32f-226">**✔️ Aumentar o intervalo de valores aceitos para uma propriedade ou parâmetro se o membro não for [virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="ab32f-227">Embora o intervalo de valores que podem ser passados ​​para o método ou retornados pelo membro possa ser expandidos, o parâmetro ou o tipo de membro não pode.</span><span class="sxs-lookup"><span data-stu-id="ab32f-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="ab32f-228">Por exemplo, enquanto os valores passados ​​para um método podem ser expandidos de 0-124 para 0-255, o tipo de parâmetro não pode ser alterado de <xref:System.Byte> para <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="ab32f-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="ab32f-229">**❌ aumentar o intervalo de valores aceitos para uma propriedade ou parâmetro se o membro for [virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="ab32f-230">Essa alteração interrompe os membros substituídos existentes, que não funcionarão corretamente para o intervalo estendido de valores.</span><span class="sxs-lookup"><span data-stu-id="ab32f-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="ab32f-231">**❌ diminuindo o intervalo de valores aceitos para uma propriedade ou parâmetro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="ab32f-232">**❌ aumentar o intervalo de valores retornados para uma propriedade, campo, valor de retorno ou parâmetro de [saída](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="ab32f-233">**❌ alterar os valores retornados para uma propriedade, campo, valor de retorno de método ou parâmetro de [saída](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="ab32f-234">**❌ alterar o valor padrão de uma propriedade, campo ou parâmetro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="ab32f-235">**❌ alterar a precisão de um valor numérico de retorno**</span><span class="sxs-lookup"><span data-stu-id="ab32f-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="ab32f-236">**❓ Uma alteração na análise de entrada e no lançamento de novas exceções (mesmo se o comportamento de análise não for especificado na documentação**</span><span class="sxs-lookup"><span data-stu-id="ab32f-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="ab32f-237">Exceções</span><span class="sxs-lookup"><span data-stu-id="ab32f-237">Exceptions</span></span>

- <span data-ttu-id="ab32f-238">**✔️ Lançar uma exceção mais derivada do que uma exceção existente**</span><span class="sxs-lookup"><span data-stu-id="ab32f-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="ab32f-239">Como a nova exceção é uma subclasse de uma exceção existente, o código de manipulação de exceção anterior continua a manipular a exceção.</span><span class="sxs-lookup"><span data-stu-id="ab32f-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="ab32f-240">Por exemplo, no .NET Framework 4, os métodos de criação e recuperação de cultura começariam a lançar um <xref:System.Globalization.CultureNotFoundException> em vez de um <xref:System.ArgumentException> se a cultura não pudesse ser encontrada.</span><span class="sxs-lookup"><span data-stu-id="ab32f-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="ab32f-241">Como <xref:System.Globalization.CultureNotFoundException> deriva de <xref:System.ArgumentException>, essa é uma alteração aceitável.</span><span class="sxs-lookup"><span data-stu-id="ab32f-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="ab32f-242">**✔️ Lançar uma exceção mais específica do que <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="ab32f-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="ab32f-243">**✔️ Lançar uma exceção que é considerada irrecuperável**</span><span class="sxs-lookup"><span data-stu-id="ab32f-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="ab32f-244">Exceções irrecuperáveis ​​não devem ser capturadas, mas precisam ser manipuladas por um manipulador de nível alto.</span><span class="sxs-lookup"><span data-stu-id="ab32f-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="ab32f-245">Portanto, não se espera que os usuários tenham código que capture essas exceções explícitas.</span><span class="sxs-lookup"><span data-stu-id="ab32f-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="ab32f-246">As exceções irrecuperáveis são:</span><span class="sxs-lookup"><span data-stu-id="ab32f-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="ab32f-247">**✔️ Lançar uma nova exceção em um novo caminho de código**</span><span class="sxs-lookup"><span data-stu-id="ab32f-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="ab32f-248">A exceção precisa se aplicar apenas a um novo caminho de código que é executado com novos valores de parâmetro ou estado e que não pode ser executado pelo código existente que tem como destino a versão anterior.</span><span class="sxs-lookup"><span data-stu-id="ab32f-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="ab32f-249">**✔️ Remover uma exceção para permitir um comportamento mais robusto ou novos cenários**</span><span class="sxs-lookup"><span data-stu-id="ab32f-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="ab32f-250">Por exemplo, um método `Divide` que anteriormente apenas manipulou valores positivos e lançou um <xref:System.ArgumentOutOfRangeException> pode ser alterado para dar suporte a valores negativos e positivos sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ab32f-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="ab32f-251">**✔️ Alterar o texto de uma mensagem de erro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="ab32f-252">Os desenvolvedores não devem se basear no texto de mensagens de erro, que também mudam com base na cultura do usuário.</span><span class="sxs-lookup"><span data-stu-id="ab32f-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="ab32f-253">**❌ lançar uma exceção em qualquer outro caso não listado acima**</span><span class="sxs-lookup"><span data-stu-id="ab32f-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="ab32f-254">**❌ remover uma exceção em qualquer outro caso não listado acima**</span><span class="sxs-lookup"><span data-stu-id="ab32f-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="ab32f-255">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab32f-255">Attributes</span></span>

- <span data-ttu-id="ab32f-256">**✔️ Alterar o valor de um atributo que é *não* observável**</span><span class="sxs-lookup"><span data-stu-id="ab32f-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="ab32f-257">**❌ alterar o valor de um atributo que *é* observável**</span><span class="sxs-lookup"><span data-stu-id="ab32f-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="ab32f-258">**❓ Remover um atributo**</span><span class="sxs-lookup"><span data-stu-id="ab32f-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="ab32f-259">Na maioria dos casos, a remoção de um atributo (como <xref:System.NonSerializedAttribute>) é uma alteração significativa.</span><span class="sxs-lookup"><span data-stu-id="ab32f-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="ab32f-260">Suporte de plataforma</span><span class="sxs-lookup"><span data-stu-id="ab32f-260">Platform support</span></span>

- <span data-ttu-id="ab32f-261">**✔️ Dar suporte a uma operação em uma plataforma que não tinha suporte anteriormente**</span><span class="sxs-lookup"><span data-stu-id="ab32f-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="ab32f-262">**❌ não dá suporte ou agora exigindo uma service pack específica para uma operação que tinha suporte anteriormente em uma plataforma**</span><span class="sxs-lookup"><span data-stu-id="ab32f-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="ab32f-263">Alterações na implementação interna</span><span class="sxs-lookup"><span data-stu-id="ab32f-263">Internal implementation changes</span></span>

- <span data-ttu-id="ab32f-264">**❓ Alterar a área de superfície de um tipo interno**</span><span class="sxs-lookup"><span data-stu-id="ab32f-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="ab32f-265">Tais mudanças geralmente são permitidas, embora interrompam a reflexão privada.</span><span class="sxs-lookup"><span data-stu-id="ab32f-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="ab32f-266">Em alguns casos, em que bibliotecas populares de terceiros ou um grande número de desenvolvedores dependem das APIs internas, essas alterações podem não ser permitidas.</span><span class="sxs-lookup"><span data-stu-id="ab32f-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="ab32f-267">**❓ Alterar a implementação interna de um membro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="ab32f-268">Essas mudanças geralmente são permitidas, embora interrompam a reflexão privada.</span><span class="sxs-lookup"><span data-stu-id="ab32f-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="ab32f-269">Em alguns casos, em que o código do cliente frequentemente depende da reflexão privada ou em que a alteração introduz efeitos colaterais indesejados, essas alterações podem não ser permitidas.</span><span class="sxs-lookup"><span data-stu-id="ab32f-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="ab32f-270">**✔️ Melhorar o desempenho de uma operação**</span><span class="sxs-lookup"><span data-stu-id="ab32f-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="ab32f-271">A capacidade de modificar o desempenho de uma operação é essencial, mas essas alterações podem quebrar o código que depende da velocidade atual de uma operação.</span><span class="sxs-lookup"><span data-stu-id="ab32f-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="ab32f-272">Isso é particularmente verdadeiro no código que depende do tempo de operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="ab32f-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="ab32f-273">A alteração de desempenho não deve afetar outros comportamentos da API em questão; caso contrário, a alteração será interrompida.</span><span class="sxs-lookup"><span data-stu-id="ab32f-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="ab32f-274">**✔️ Alterar indiretamente (e, muitas vezes, adversamente) o desempenho de uma operação**</span><span class="sxs-lookup"><span data-stu-id="ab32f-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="ab32f-275">Se a alteração em questão não for categorizada como significativa por algum outro motivo, isso será aceitável.</span><span class="sxs-lookup"><span data-stu-id="ab32f-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="ab32f-276">Geralmente, ações precisam ser realizadas, o que pode incluir operações extras ou a adição de novas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="ab32f-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="ab32f-277">Isso quase sempre afetará o desempenho, mas pode ser essencial para que a API em questão funcione conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="ab32f-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="ab32f-278">**❌ alterar uma API síncrona para assíncrona (e vice-versa)**</span><span class="sxs-lookup"><span data-stu-id="ab32f-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="ab32f-279">Alterações de código</span><span class="sxs-lookup"><span data-stu-id="ab32f-279">Code changes</span></span>

- <span data-ttu-id="ab32f-280">**✔️ Adicionar [parâmetros](../../csharp/language-reference/keywords/params.md) a um parâmetro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="ab32f-281">**❌ alterar uma [struct](../../csharp/language-reference/keywords/struct.md) para uma [classe](../../csharp/language-reference/keywords/class.md) e vice-versa**</span><span class="sxs-lookup"><span data-stu-id="ab32f-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="ab32f-282">**❌ adicionar a palavra-chave [Checked](../../csharp/language-reference/keywords/virtual.md) a um bloco de código**</span><span class="sxs-lookup"><span data-stu-id="ab32f-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="ab32f-283">Essa alteração pode fazer com que um código que foi executado anteriormente lance um <xref:System.OverflowException>, o que é inaceitável.</span><span class="sxs-lookup"><span data-stu-id="ab32f-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="ab32f-284">**❌ remover [params](../../csharp/language-reference/keywords/params.md) de um parâmetro**</span><span class="sxs-lookup"><span data-stu-id="ab32f-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="ab32f-285">**❌ alterar a ordem na qual os eventos são acionados**</span><span class="sxs-lookup"><span data-stu-id="ab32f-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="ab32f-286">Os desenvolvedores podem razoavelmente esperar que os eventos sejam disparados na mesma ordem, e o código do desenvolvedor frequentemente depende da ordem em que os eventos são disparados.</span><span class="sxs-lookup"><span data-stu-id="ab32f-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="ab32f-287">**❌ remover a geração de um evento em uma determinada ação**</span><span class="sxs-lookup"><span data-stu-id="ab32f-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="ab32f-288">**❌ alterar o número de vezes que os eventos fornecidos são chamados**</span><span class="sxs-lookup"><span data-stu-id="ab32f-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="ab32f-289">**❌ adicionar o <xref:System.FlagsAttribute> a um tipo de enumeração**</span><span class="sxs-lookup"><span data-stu-id="ab32f-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
