---
title: Tipos de alterações da falha
description: Saiba como o .NET Core tenta manter a compatibilidade para desenvolvedores em versões .NET e que tipo de mudança é considerada uma mudança de ruptura.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628586"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="fe71c-103">Mudanças que afetam a compatibilidade</span><span class="sxs-lookup"><span data-stu-id="fe71c-103">Changes that affect compatibility</span></span>

<span data-ttu-id="fe71c-104">Ao longo de sua história, o .NET tentou manter um alto nível de compatibilidade de versão para versão e em todos os tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="fe71c-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="fe71c-105">Isso também ocorre no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe71c-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="fe71c-106">Embora o .NET Core possa ser considerado uma nova tecnologia independente do .NET Framework, dois fatores principais limitam a capacidade do .NET Core de divergir do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fe71c-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="fe71c-107">Um grande número de desenvolvedores originalmente desenvolveu ou continua a desenvolver aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe71c-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="fe71c-108">Eles esperam um comportamento consistente nas implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="fe71c-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="fe71c-109">Os projetos da biblioteca .NET Standard permitem que os desenvolvedores criem bibliotecas voltadas a APIs comuns compartilhadas pelo .NET Core e pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe71c-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="fe71c-110">Os desenvolvedores esperam que uma biblioteca usada em um aplicativo .NET Core se comporte de maneira idêntica à mesma biblioteca usada em um aplicativo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe71c-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="fe71c-111">Além da compatibilidade entre as implementações do .NET, os desenvolvedores esperam um alto nível de compatibilidade nas versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe71c-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="fe71c-112">Em particular, o código escrito para uma versão anterior do .NET Core precisam ser executado sem problemas em uma versão posterior do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe71c-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="fe71c-113">Na verdade, muitos desenvolvedores esperam que as novas APIs encontradas em versões recém-lançadas do .NET Core também sejam compatíveis com as versões de pré-lançamento em que essas APIs foram apresentadas.</span><span class="sxs-lookup"><span data-stu-id="fe71c-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="fe71c-114">Este artigo descreve as categorias de alterações de compatibilidade (ou alterações significativas) e a maneira como a equipe do .NET avalia alterações em cada uma dessas categorias.</span><span class="sxs-lookup"><span data-stu-id="fe71c-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="fe71c-115">Entender como a equipe do .NET aborda possíveis mudanças de quebra é particularmente útil para desenvolvedores que abrem solicitações de puxar no repositório [Dotnet/runtime](https://github.com/dotnet/runtime) GitHub que modificam o comportamento das APIs existentes.</span><span class="sxs-lookup"><span data-stu-id="fe71c-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="fe71c-116">Para obter uma definição das categorias de compatibilidade, como compatibilidade binária e compatibilidade com versões anteriores, confira [Categorias de alterações significativas](categories.md).</span><span class="sxs-lookup"><span data-stu-id="fe71c-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="fe71c-117">As seções a seguir descrevem as categorias de alterações feitas nas APIs do Núcleo .NET e seu impacto na compatibilidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe71c-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="fe71c-118">As mudanças são permitidas ❌✔️, proibidas, ou requerem julgamento e uma avaliação de quão previsível, óbvio e consistente o comportamento anterior foi ❓.</span><span class="sxs-lookup"><span data-stu-id="fe71c-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="fe71c-119">Além de servir como um guia de como as alterações nas bibliotecas .NET Core são avaliadas, os desenvolvedores de bibliotecas também podem usar esses critérios para avaliar as alterações em suas bibliotecas voltadas a várias implementações e versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="fe71c-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="fe71c-120">Modificações no contrato público</span><span class="sxs-lookup"><span data-stu-id="fe71c-120">Modifications to the public contract</span></span>

<span data-ttu-id="fe71c-121">Alterações nesta categoria modificam a área de superfície pública de um tipo.</span><span class="sxs-lookup"><span data-stu-id="fe71c-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="fe71c-122">A maioria das alterações nesta categoria não é permitida porque viola a *compatibilidade com versões anteriores* (a capacidade de um aplicativo desenvolvido com a versão anterior de uma API ser executado sem recompilação em uma versão posterior).</span><span class="sxs-lookup"><span data-stu-id="fe71c-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="fe71c-123">Tipos</span><span class="sxs-lookup"><span data-stu-id="fe71c-123">Types</span></span>

- <span data-ttu-id="fe71c-124">✔️ **PERMITIDO: Remover uma implementação de interface de um tipo quando a interface já é implementada por um tipo de base**</span><span class="sxs-lookup"><span data-stu-id="fe71c-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="fe71c-125">❓ **REQUER JULGAMENTO: Adicionar uma nova implementação de interface a um tipo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="fe71c-126">Essa é uma alteração aceitável, pois não afeta negativamente os clientes existentes.</span><span class="sxs-lookup"><span data-stu-id="fe71c-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="fe71c-127">Quaisquer alterações no tipo precisam funcionar dentro dos limites das alterações aceitáveis ​​definidas aqui para que a nova implementação permaneça aceitável.</span><span class="sxs-lookup"><span data-stu-id="fe71c-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="fe71c-128">É necessário ter um extremo cuidado ao adicionar interfaces que afetam diretamente a capacidade de um designer ou serializador de gerar código ou dados que não podem ser consumidos em um nível anterior.</span><span class="sxs-lookup"><span data-stu-id="fe71c-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="fe71c-129">Um exemplo é a interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="fe71c-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="fe71c-130">❓ **REQUER JULGAMENTO: Introdução de uma nova classe base**</span><span class="sxs-lookup"><span data-stu-id="fe71c-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="fe71c-131">Um tipo pode ser introduzido em uma hierarquia entre dois tipos existentes se não introduzir novos membros [abstratos](../../csharp/language-reference/keywords/abstract.md) ou alterar a semântica ou comportamento dos tipos existentes.</span><span class="sxs-lookup"><span data-stu-id="fe71c-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="fe71c-132">Por exemplo, no .NET Framework 2.0, a classe <xref:System.Data.Common.DbConnection> tornou-se uma nova classe base para <xref:System.Data.SqlClient.SqlConnection>, que antes era derivada diretamente de <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="fe71c-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="fe71c-133">✔️ **PERMITIDO: Mover um tipo de uma montagem para outra**</span><span class="sxs-lookup"><span data-stu-id="fe71c-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="fe71c-134">A *antiga* assembléia deve <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> ser marcada com o que aponta para a nova assembléia.</span><span class="sxs-lookup"><span data-stu-id="fe71c-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="fe71c-135">✔️ **PERMITIDO: Mudar um tipo `readonly struct` de [estrutura](../../csharp/language-reference/builtin-types/struct.md) para um tipo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="fe71c-136">Não `readonly struct` é permitido `struct` mudar um tipo para um tipo.</span><span class="sxs-lookup"><span data-stu-id="fe71c-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="fe71c-137">✔️ **permitido: Adicionar a palavra-chave [selada](../../csharp/language-reference/keywords/sealed.md) ou [abstrata](../../csharp/language-reference/keywords/abstract.md) a um tipo quando não há construtores *acessíveis* (públicos ou protegidos)**</span><span class="sxs-lookup"><span data-stu-id="fe71c-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="fe71c-138">✔️ **permitido: Expandir a visibilidade de um tipo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="fe71c-139">❌**Proibido: Alterando o namespace ou nome de um tipo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="fe71c-140">❌**Desautorizado: Renomear ou remover um tipo público**</span><span class="sxs-lookup"><span data-stu-id="fe71c-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="fe71c-141">Isso interrompe todo o código que usa o tipo renomeado ou removido.</span><span class="sxs-lookup"><span data-stu-id="fe71c-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="fe71c-142">❌**Desautorizado: Alterando o tipo subjacente de uma enumeração**</span><span class="sxs-lookup"><span data-stu-id="fe71c-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="fe71c-143">Esta é uma alteração significativa de tempo de compilação e comportamental, bem como uma alteração significativa binária que pode tornar os argumentos de atributo inseparáveis.</span><span class="sxs-lookup"><span data-stu-id="fe71c-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="fe71c-144">❌**Proibido: Selando um tipo que foi anteriormente não selado**</span><span class="sxs-lookup"><span data-stu-id="fe71c-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="fe71c-145">❌**Desautorizado: Adicionando uma interface ao conjunto de tipos de base de uma interface**</span><span class="sxs-lookup"><span data-stu-id="fe71c-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="fe71c-146">Se uma interface implementar uma interface não implementada anteriormente, todos os tipos que implementaram a versão original da interface serão corrompidos.</span><span class="sxs-lookup"><span data-stu-id="fe71c-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="fe71c-147">❓ **REQUER JULGAMENTO: Remoção de uma classe do conjunto de classes base ou de uma interface do conjunto de interfaces implementadas**</span><span class="sxs-lookup"><span data-stu-id="fe71c-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="fe71c-148">Há uma exceção à regra para remoção de interface: é possível adicionar a implementação de uma interface derivada da interface removida.</span><span class="sxs-lookup"><span data-stu-id="fe71c-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="fe71c-149">Por exemplo, você pode remover <xref:System.IDisposable> se o tipo ou interface agora implementa <xref:System.ComponentModel.IComponent>, que implementa <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="fe71c-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="fe71c-150">❌\*\*Proibido: Mudar um `readonly struct` tipo para um tipo [de estrutura](../../csharp/language-reference/builtin-types/struct.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="fe71c-151">A mudança `struct` de um `readonly struct` tipo para um tipo é permitida, no entanto.</span><span class="sxs-lookup"><span data-stu-id="fe71c-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="fe71c-152">❌**Proibido: Mudar um tipo [de](../../csharp/language-reference/builtin-types/struct.md) estrutura `ref struct` para um tipo, e vice-versa**</span><span class="sxs-lookup"><span data-stu-id="fe71c-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="fe71c-153">❌**Desautorizado: Reduzindo a visibilidade de um tipo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="fe71c-154">No entanto, aumentar a visibilidade de um tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="fe71c-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="fe71c-155">Membros</span><span class="sxs-lookup"><span data-stu-id="fe71c-155">Members</span></span>

- <span data-ttu-id="fe71c-156">✔️ \*\*PERMITIDO: Expandir a visibilidade de um membro que não é [virtual](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="fe71c-157">✔️ \*\*permitido: Adicionar um membro abstrato a um tipo público que não tenha construtores *acessíveis* (públicos ou protegidos) ou o tipo seja [selado](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="fe71c-158">No entanto, adicionar um membro abstrato a um tipo que tenha construtores acessíveis (públicos ou protegidos) e não seja `sealed` não é permitido.</span><span class="sxs-lookup"><span data-stu-id="fe71c-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="fe71c-159">✔️ \*\*permitido: Restringir a visibilidade de um membro [protegido](../../csharp/language-reference/keywords/protected.md) quando o tipo não tiver construtores acessíveis (públicos ou protegidos) ou o tipo for [selado](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="fe71c-160">✔️ **permitido: Mover um membro para uma classe mais alta na hierarquia do que o tipo de qual foi removido**</span><span class="sxs-lookup"><span data-stu-id="fe71c-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="fe71c-161">✔️ **PERMITIDO: Adicionar ou remover uma substituição**</span><span class="sxs-lookup"><span data-stu-id="fe71c-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="fe71c-162">A introdução de uma substituição pode fazer com que os consumidores anteriores pulem a substituição ao chamar [a base](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="fe71c-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="fe71c-163">✔️ **permitido: Adicionar um construtor a uma classe, juntamente com um construtor sem parâmetros se a classe anteriormente não tivesse construtores**</span><span class="sxs-lookup"><span data-stu-id="fe71c-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="fe71c-164">No entanto, não é permitido adicionar um construtor a uma classe que anteriormente não tinha construtores *sem* adicionar o construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fe71c-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="fe71c-165">✔️ \*\*permitido: Mudar um membro de [abstrato](../../csharp/language-reference/keywords/abstract.md) para [virtual](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="fe71c-166">✔️ **PERMITIDO: Mudar `ref readonly` de `ref` um para um valor de retorno (exceto para métodos ou interfaces virtuais)**</span><span class="sxs-lookup"><span data-stu-id="fe71c-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="fe71c-167">✔️ **PERMITIDO: Remover [leitura somente](../../csharp/language-reference/keywords/readonly.md) de um campo, a menos que o tipo estático do campo seja um tipo de valor mutável**</span><span class="sxs-lookup"><span data-stu-id="fe71c-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="fe71c-168">✔️ **permitido: Chamar um novo evento que não foi definido anteriormente**</span><span class="sxs-lookup"><span data-stu-id="fe71c-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="fe71c-169">❓ **REQUER JULGAMENTO: Adicionar um novo campo de instância a um tipo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="fe71c-170">Essa alteração afeta a serialização.</span><span class="sxs-lookup"><span data-stu-id="fe71c-170">This change impacts serialization.</span></span>

- <span data-ttu-id="fe71c-171">❌**Desautorizado: Renomear ou remover um membro público ou parâmetro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="fe71c-172">Isso interrompe todo o código que usa o membro ou parâmetro renomeado ou removido.</span><span class="sxs-lookup"><span data-stu-id="fe71c-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="fe71c-173">Isso inclui remover ou renomear um getter ou setter de uma propriedade, bem como renomear ou remover membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="fe71c-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="fe71c-174">❌**Proibido: Adicionar um membro a uma interface**</span><span class="sxs-lookup"><span data-stu-id="fe71c-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="fe71c-175">❌**Desautorizado: Alterar o valor de um membro público constante ou enumeração**</span><span class="sxs-lookup"><span data-stu-id="fe71c-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="fe71c-176">❌**Desautorizado: Alterando o tipo de propriedade, campo, parâmetro ou valor de devolução**</span><span class="sxs-lookup"><span data-stu-id="fe71c-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="fe71c-177">❌**Desautorizado: Adicionar, remover ou alterar a ordem dos parâmetros**</span><span class="sxs-lookup"><span data-stu-id="fe71c-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="fe71c-178">❌**Desautorizado: Adicionar ou remover a [palavra-chave in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) ou [ref](../../csharp/language-reference/keywords/ref.md) de um parâmetro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="fe71c-179">❌**Desautorizado: Renomeando um parâmetro (incluindo a alteração de seu caso)**</span><span class="sxs-lookup"><span data-stu-id="fe71c-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="fe71c-180">Isso é considerado significativo por dois motivos:</span><span class="sxs-lookup"><span data-stu-id="fe71c-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="fe71c-181">Interrompe cenários de associação tardia, como o recurso de associação tardia no Visual Basic e [dinâmico](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) no C#.</span><span class="sxs-lookup"><span data-stu-id="fe71c-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="fe71c-182">Interrompe a [compatibilidade de origem](categories.md#source-compatibility) quando os desenvolvedores usam [argumentos nomeados](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="fe71c-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="fe71c-183">❌**Desautorizado: Alterando `ref` de um `ref readonly` valor de retorno para um valor de retorno**</span><span class="sxs-lookup"><span data-stu-id="fe71c-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="fe71c-184">❌️**Desautorizado: Mudando `ref readonly` de `ref` um para um valor de retorno em um método ou interface virtual**</span><span class="sxs-lookup"><span data-stu-id="fe71c-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="fe71c-185">❌**Proibido: Adicionar ou remover [resumo](../../csharp/language-reference/keywords/abstract.md) de um membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="fe71c-186">❌**Proibido: Remoção da palavra-chave [virtual](../../csharp/language-reference/keywords/virtual.md) de um membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="fe71c-187">Embora isso geralmente não seja uma alteração significativa, pois o compilador C# tende a emitir instruções [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) de IL (Intermediate Language) para chamar métodos não virtuais (`callvirt` executa uma verificação nula, enquanto uma chamada normal não), esse comportamento não é invariável por vários motivos:</span><span class="sxs-lookup"><span data-stu-id="fe71c-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="fe71c-188">C# não é a única linguagem de destino do .NET.</span><span class="sxs-lookup"><span data-stu-id="fe71c-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="fe71c-189">O compilador C# tenta otimizar cada vez mais `callvirt` a uma chamada normal sempre que o método de destino é não virtual e provavelmente não é nulo (como um método acessado por meio de operador de propagação nula [?.](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="fe71c-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="fe71c-190">Tornar um método virtual significa que o código do consumidor em geral acabaria chamando-o não virtualmente.</span><span class="sxs-lookup"><span data-stu-id="fe71c-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="fe71c-191">❌**Proibido: Adicionar a palavra-chave [virtual](../../csharp/language-reference/keywords/virtual.md) a um membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="fe71c-192">❌**Proibido: Fazer um membro virtual abstrato**</span><span class="sxs-lookup"><span data-stu-id="fe71c-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="fe71c-193">Um [membro virtual](../../csharp/language-reference/keywords/virtual.md) fornece uma implementação de método que *pode ser* substituída por uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="fe71c-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="fe71c-194">Um [membro abstrato](../../csharp/language-reference/keywords/abstract.md) não fornece nenhuma implementação e *precisa ser* substituído.</span><span class="sxs-lookup"><span data-stu-id="fe71c-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="fe71c-195">❌\*\*Desautorizado: Adicionar um membro abstrato a um tipo público que tenha construtores acessíveis (públicos ou protegidos) e que não seja [selado](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="fe71c-196">❌**Proibido: Adicionar ou remover a [palavra-chave estática](../../csharp/language-reference/keywords/static.md) de um membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="fe71c-197">❌**Despermitido: Adicionar uma sobrecarga que impeça uma sobrecarga existente e define um comportamento diferente**</span><span class="sxs-lookup"><span data-stu-id="fe71c-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="fe71c-198">Isso interrompe os clientes existentes que estavam vinculados à sobrecarga anterior.</span><span class="sxs-lookup"><span data-stu-id="fe71c-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="fe71c-199">Por exemplo, se uma classe tiver uma única versão de um método que aceite um <xref:System.UInt32>, um consumidor existente será vinculado a essa sobrecarga ao passar um valor <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="fe71c-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="fe71c-200">No entanto, se você adicionar uma sobrecarga que aceita um <xref:System.Int32>, ao recompilar ou usar associação tardia, o compilador agora se associa à nova sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="fe71c-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="fe71c-201">Se resultar em um comportamento diferente, significa que essa é uma alteração significativa.</span><span class="sxs-lookup"><span data-stu-id="fe71c-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="fe71c-202">❌**Proibido: Adicionar um construtor a uma classe que anteriormente não tinha construtor sem adicionar o construtor sem parâmetros**</span><span class="sxs-lookup"><span data-stu-id="fe71c-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="fe71c-203">❌️**Proibido: Adicionar [leitura apenas](../../csharp/language-reference/keywords/readonly.md) a um campo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="fe71c-204">❌**Desautorizado: Reduzindo a visibilidade de um membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="fe71c-205">Isso inclui reduzir a visibilidade de um membro [protegido](../../csharp/language-reference/keywords/protected.md) quando há construtores *acessíveis* `public` (ou `protected`) e o tipo *não* é [selado](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="fe71c-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="fe71c-206">Se esse não for o caso, será permitido reduzir a visibilidade de um membro protegido.</span><span class="sxs-lookup"><span data-stu-id="fe71c-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="fe71c-207">Aumentar a visibilidade de um membro é permitido.</span><span class="sxs-lookup"><span data-stu-id="fe71c-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="fe71c-208">❌**Proibido: Mudar o tipo de membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="fe71c-209">Não é possível modificar o valor de retorno de um método ou o tipo de uma propriedade ou campo.</span><span class="sxs-lookup"><span data-stu-id="fe71c-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="fe71c-210">Por exemplo, a assinatura de um método que retorna um <xref:System.Object> não pode ser alterada para retornar um <xref:System.String> ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="fe71c-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="fe71c-211">❌**Proibido: Adicionar um campo a uma estrutura que anteriormente não tinha estado**</span><span class="sxs-lookup"><span data-stu-id="fe71c-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="fe71c-212">As regras de atribuição definidas permitem o uso de variáveis ​​não inicializadas, desde que o tipo de variável seja um struct sem estado.</span><span class="sxs-lookup"><span data-stu-id="fe71c-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="fe71c-213">Se o struct for alterado para “com estado”, o código poderá acabar com dados não inicializados.</span><span class="sxs-lookup"><span data-stu-id="fe71c-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="fe71c-214">Isso é potencialmente uma interrupção de fonte e uma alteração binária significativa.</span><span class="sxs-lookup"><span data-stu-id="fe71c-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="fe71c-215">❌**Desautorizado: Disparar um evento existente quando nunca foi disparado antes**</span><span class="sxs-lookup"><span data-stu-id="fe71c-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="fe71c-216">Alterações de comportamento</span><span class="sxs-lookup"><span data-stu-id="fe71c-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="fe71c-217">Assemblies</span><span class="sxs-lookup"><span data-stu-id="fe71c-217">Assemblies</span></span>

- <span data-ttu-id="fe71c-218">✔️ **permitido: Tornar um conjunto portátil quando as mesmas plataformas ainda são suportadas**</span><span class="sxs-lookup"><span data-stu-id="fe71c-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="fe71c-219">❌**Proibido: Mudar o nome de uma assembléia**</span><span class="sxs-lookup"><span data-stu-id="fe71c-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="fe71c-220">❌**Proibido: Mudar a chave pública de uma assembléia**</span><span class="sxs-lookup"><span data-stu-id="fe71c-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="fe71c-221">Propriedades, campos, parâmetros e valores retornados</span><span class="sxs-lookup"><span data-stu-id="fe71c-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="fe71c-222">✔️ **permitido: Alterar o valor de um imóvel, campo, valor de retorno ou parâmetro [de saída](../../csharp/language-reference/keywords/out-parameter-modifier.md) para um tipo mais derivado**</span><span class="sxs-lookup"><span data-stu-id="fe71c-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="fe71c-223">Por exemplo, um método que retorna um tipo de <xref:System.Object> pode retornar uma instância <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="fe71c-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="fe71c-224">(No entanto, a assinatura do método não pode ser alterada.)</span><span class="sxs-lookup"><span data-stu-id="fe71c-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="fe71c-225">✔️ \*\*permitido: Aumentar a gama de valores aceitos para uma propriedade ou parâmetro se o membro não for [virtual](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="fe71c-226">Embora a gama de valores que podem ser repassados ao método ou são devolvidos pelo membro possa se expandir, o parâmetro ou tipo de membro não pode.</span><span class="sxs-lookup"><span data-stu-id="fe71c-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="fe71c-227">Por exemplo, enquanto os valores passados ​​para um método podem ser expandidos de 0-124 para 0-255, o tipo de parâmetro não pode ser alterado de <xref:System.Byte> para <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="fe71c-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="fe71c-228">❌\*\*Desautorizado: Aumentar a gama de valores aceitos para uma propriedade ou parâmetro se o membro for [virtual](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="fe71c-229">Essa alteração interrompe os membros substituídos existentes, que não funcionarão corretamente para o intervalo estendido de valores.</span><span class="sxs-lookup"><span data-stu-id="fe71c-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="fe71c-230">❌**Desautorizado: Diminuindo a gama de valores aceitos para um imóvel ou parâmetro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="fe71c-231">❌\*\*Desautorizado: Aumentar a gama de valores devolvidos para um imóvel, campo, valor de retorno ou parâmetro [de saída](../../csharp/language-reference/keywords/out-parameter-modifier.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="fe71c-232">❌\*\*Desautorizado: Alterando os valores devolvidos para um valor de retorno de propriedade, campo, método ou parâmetro [de saída](../../csharp/language-reference/keywords/out-parameter-modifier.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="fe71c-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="fe71c-233">❌**Proibido: Alterar o valor padrão de um imóvel, campo ou parâmetro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="fe71c-234">❌**Desautorizado: Alterando a precisão de um valor de retorno numérico**</span><span class="sxs-lookup"><span data-stu-id="fe71c-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="fe71c-235">❓ **REQUER JULGAMENTO: Uma mudança no parsing de entrada e lançamento de novas exceções (mesmo que o comportamento de análise não esteja especificado na documentação**</span><span class="sxs-lookup"><span data-stu-id="fe71c-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="fe71c-236">Exceções</span><span class="sxs-lookup"><span data-stu-id="fe71c-236">Exceptions</span></span>

- <span data-ttu-id="fe71c-237">✔️ **permitido: Lançar uma exceção mais derivada do que uma exceção existente**</span><span class="sxs-lookup"><span data-stu-id="fe71c-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="fe71c-238">Como a nova exceção é uma subclasse de uma exceção existente, o código de manipulação de exceção anterior continua a manipular a exceção.</span><span class="sxs-lookup"><span data-stu-id="fe71c-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="fe71c-239">Por exemplo, no .NET Framework 4, os métodos de criação e recuperação de cultura começariam a lançar um <xref:System.Globalization.CultureNotFoundException> em vez de um <xref:System.ArgumentException> se a cultura não pudesse ser encontrada.</span><span class="sxs-lookup"><span data-stu-id="fe71c-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="fe71c-240">Como <xref:System.Globalization.CultureNotFoundException> deriva de <xref:System.ArgumentException>, essa é uma alteração aceitável.</span><span class="sxs-lookup"><span data-stu-id="fe71c-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="fe71c-241">✔️ **permitido: Lançar uma <xref:System.NotSupportedException>exceção <xref:System.NullReferenceException> mais específica do que , <xref:System.NotImplementedException>**</span><span class="sxs-lookup"><span data-stu-id="fe71c-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="fe71c-242">✔️ **PERMITIDO: Lançar uma exceção que é considerada irrecuperável**</span><span class="sxs-lookup"><span data-stu-id="fe71c-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="fe71c-243">Exceções irrecuperáveis ​​não devem ser capturadas, mas precisam ser manipuladas por um manipulador de nível alto.</span><span class="sxs-lookup"><span data-stu-id="fe71c-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="fe71c-244">Portanto, não se espera que os usuários tenham código que capture essas exceções explícitas.</span><span class="sxs-lookup"><span data-stu-id="fe71c-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="fe71c-245">As exceções irrecuperáveis são:</span><span class="sxs-lookup"><span data-stu-id="fe71c-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="fe71c-246">✔️ **permitido: Lançar uma nova exceção em um novo caminho de código**</span><span class="sxs-lookup"><span data-stu-id="fe71c-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="fe71c-247">A exceção deve ser aplicada apenas a um novo caminho de código que é executado com novos valores de parâmetro ou estado e que não pode ser executado pelo código existente que tem como alvo a versão anterior.</span><span class="sxs-lookup"><span data-stu-id="fe71c-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="fe71c-248">✔️ **permitido: Remover uma exceção para permitir comportamentos mais robustos ou novos cenários**</span><span class="sxs-lookup"><span data-stu-id="fe71c-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="fe71c-249">Por exemplo, um método `Divide` que anteriormente apenas manipulou valores positivos e lançou um <xref:System.ArgumentOutOfRangeException> pode ser alterado para dar suporte a valores negativos e positivos sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fe71c-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="fe71c-250">✔️ **PERMITIDO: Alterar o texto de uma mensagem de erro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="fe71c-251">Os desenvolvedores não devem se basear no texto de mensagens de erro, que também mudam com base na cultura do usuário.</span><span class="sxs-lookup"><span data-stu-id="fe71c-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="fe71c-252">❌**Desautorizado: Abrir uma exceção em qualquer outro caso não listado acima**</span><span class="sxs-lookup"><span data-stu-id="fe71c-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="fe71c-253">❌**Desautorizado: Remoção de uma exceção em qualquer outro caso não listado acima**</span><span class="sxs-lookup"><span data-stu-id="fe71c-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="fe71c-254">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe71c-254">Attributes</span></span>

- <span data-ttu-id="fe71c-255">✔️ **PERMITIDO: Alterar o valor de um atributo que *não* é observável**</span><span class="sxs-lookup"><span data-stu-id="fe71c-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="fe71c-256">❌**Desautorizado: Alterando o valor de um atributo que *é* observável**</span><span class="sxs-lookup"><span data-stu-id="fe71c-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="fe71c-257">❓ **REQUER JULGAMENTO: Remoção de um atributo**</span><span class="sxs-lookup"><span data-stu-id="fe71c-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="fe71c-258">Na maioria dos casos, a remoção de um atributo (como <xref:System.NonSerializedAttribute>) é uma alteração significativa.</span><span class="sxs-lookup"><span data-stu-id="fe71c-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="fe71c-259">Suporte a plataforma</span><span class="sxs-lookup"><span data-stu-id="fe71c-259">Platform support</span></span>

- <span data-ttu-id="fe71c-260">✔️ **permitido: Apoiar uma operação em uma plataforma que anteriormente não era suportada**</span><span class="sxs-lookup"><span data-stu-id="fe71c-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="fe71c-261">❌**Proibido: Não suportar ou agora exigir um pacote de serviço específico para uma operação que foi anteriormente suportada em uma plataforma**</span><span class="sxs-lookup"><span data-stu-id="fe71c-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="fe71c-262">Alterações na implementação interna</span><span class="sxs-lookup"><span data-stu-id="fe71c-262">Internal implementation changes</span></span>

- <span data-ttu-id="fe71c-263">❓ **REQUER JULGAMENTO: Alterando a área de superfície de um tipo interno**</span><span class="sxs-lookup"><span data-stu-id="fe71c-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="fe71c-264">Tais mudanças geralmente são permitidas, embora interrompam a reflexão privada.</span><span class="sxs-lookup"><span data-stu-id="fe71c-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="fe71c-265">Em alguns casos, em que bibliotecas populares de terceiros ou um grande número de desenvolvedores dependem das APIs internas, essas alterações podem não ser permitidas.</span><span class="sxs-lookup"><span data-stu-id="fe71c-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="fe71c-266">❓ **REQUER JULGAMENTO: Alterando a implementação interna de um membro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="fe71c-267">Essas mudanças geralmente são permitidas, embora interrompam a reflexão privada.</span><span class="sxs-lookup"><span data-stu-id="fe71c-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="fe71c-268">Em alguns casos, em que o código do cliente frequentemente depende da reflexão privada ou em que a alteração introduz efeitos colaterais indesejados, essas alterações podem não ser permitidas.</span><span class="sxs-lookup"><span data-stu-id="fe71c-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="fe71c-269">✔️ **PERMITIDO: Melhorar o desempenho de uma operação**</span><span class="sxs-lookup"><span data-stu-id="fe71c-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="fe71c-270">A capacidade de modificar o desempenho de uma operação é essencial, mas essas alterações podem quebrar o código que depende da velocidade atual de uma operação.</span><span class="sxs-lookup"><span data-stu-id="fe71c-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="fe71c-271">Isso é particularmente verdadeiro no código que depende do tempo de operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="fe71c-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="fe71c-272">A mudança de desempenho não deve ter efeito sobre outros comportamentos da API em questão; caso contrário, a mudança será quebrando.</span><span class="sxs-lookup"><span data-stu-id="fe71c-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="fe71c-273">✔️ **PERMITIDO: Indiretamente (e muitas vezes adversamente) alterando o desempenho de uma operação**</span><span class="sxs-lookup"><span data-stu-id="fe71c-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="fe71c-274">Se a alteração em questão não for categorizada como significativa por algum outro motivo, isso será aceitável.</span><span class="sxs-lookup"><span data-stu-id="fe71c-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="fe71c-275">Geralmente, ações precisam ser realizadas, o que pode incluir operações extras ou a adição de novas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="fe71c-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="fe71c-276">Isso quase sempre afetará o desempenho, mas pode ser essencial para que a API em questão funcione conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="fe71c-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="fe71c-277">❌**Desautorizado: Alterando uma API síncrona para assíncrona (e vice-versa)**</span><span class="sxs-lookup"><span data-stu-id="fe71c-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="fe71c-278">Alterações de código</span><span class="sxs-lookup"><span data-stu-id="fe71c-278">Code changes</span></span>

- <span data-ttu-id="fe71c-279">✔️ **permitido: Adicionar [params](../../csharp/language-reference/keywords/params.md) a um parâmetro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="fe71c-280">❌**Proibido: Mudar uma [estrutura](../../csharp/language-reference/builtin-types/struct.md) para uma [classe](../../csharp/language-reference/keywords/class.md) e vice-versa**</span><span class="sxs-lookup"><span data-stu-id="fe71c-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="fe71c-281">❌**Proibido: Adicionar a palavra-chave [verificada](../../csharp/language-reference/keywords/virtual.md) a um bloco de código**</span><span class="sxs-lookup"><span data-stu-id="fe71c-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="fe71c-282">Essa alteração pode fazer com que um código que foi executado anteriormente lance um <xref:System.OverflowException>, o que é inaceitável.</span><span class="sxs-lookup"><span data-stu-id="fe71c-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="fe71c-283">❌**Proibido: Remoção [de params](../../csharp/language-reference/keywords/params.md) de um parâmetro**</span><span class="sxs-lookup"><span data-stu-id="fe71c-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="fe71c-284">❌**Proibido: Alterando a ordem em que os eventos são disparados**</span><span class="sxs-lookup"><span data-stu-id="fe71c-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="fe71c-285">Os desenvolvedores podem razoavelmente esperar que os eventos sejam disparados na mesma ordem, e o código do desenvolvedor frequentemente depende da ordem em que os eventos são disparados.</span><span class="sxs-lookup"><span data-stu-id="fe71c-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="fe71c-286">❌**Proibido: Remoção da criação de um evento em uma determinada ação**</span><span class="sxs-lookup"><span data-stu-id="fe71c-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="fe71c-287">❌**Proibido: Alterar o número de vezes que os eventos são chamados**</span><span class="sxs-lookup"><span data-stu-id="fe71c-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="fe71c-288">❌**Desautorizado: Adicionar <xref:System.FlagsAttribute> o tipo de enumeração**</span><span class="sxs-lookup"><span data-stu-id="fe71c-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
