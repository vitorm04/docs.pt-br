---
title: Controle de versão de C# – Guia de C#
description: Compreender o funcionamento do controle de versão em C# e .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: bfad7abe6b2b5c6a19324656963a79212a317110
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926589"
---
# <a name="versioning-in-c"></a><span data-ttu-id="768f3-103">Controle de versão em C\#</span><span class="sxs-lookup"><span data-stu-id="768f3-103">Versioning in C\#</span></span>

<span data-ttu-id="768f3-104">Neste tutorial, você aprenderá o que significa o controle de versão no .NET.</span><span class="sxs-lookup"><span data-stu-id="768f3-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="768f3-105">Você também aprenderá sobre os fatores a serem considerados ao fazer o controle de versão de sua biblioteca, bem como ao atualizar para uma nova versão de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="768f3-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="768f3-106">Criando bibliotecas</span><span class="sxs-lookup"><span data-stu-id="768f3-106">Authoring Libraries</span></span>

<span data-ttu-id="768f3-107">Como um desenvolvedor que criou a bibliotecas .NET para uso público, provavelmente você esteve em situações em que precisa distribuir novas atualizações.</span><span class="sxs-lookup"><span data-stu-id="768f3-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="768f3-108">Como você realiza esse processo é muito importante, pois você precisa garantir que haja uma transição suave do código existente para a nova versão da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="768f3-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="768f3-109">Aqui estão Vários aspectos a considerar ao criar uma nova versão:</span><span class="sxs-lookup"><span data-stu-id="768f3-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="768f3-110">Controle de Versão Semântico</span><span class="sxs-lookup"><span data-stu-id="768f3-110">Semantic Versioning</span></span>

<span data-ttu-id="768f3-111">[Controle de versão semântico](https://semver.org/) (SemVer, de forma abreviada) é uma convenção de nomenclatura aplicada a versões de sua biblioteca para indicar eventos com marcos específicos.</span><span class="sxs-lookup"><span data-stu-id="768f3-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="768f3-112">Idealmente, as informações de versão que você fornece a sua biblioteca devem ajudar os desenvolvedores a determinar a compatibilidade com seus projetos que usam versões mais antigas da mesma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="768f3-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="768f3-113">A abordagem mais básica ao SemVer é o formato de 3 componentes `MAJOR.MINOR.PATCH`, em que:</span><span class="sxs-lookup"><span data-stu-id="768f3-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="768f3-114">`MAJOR` é incrementado quando você faz alterações em APIs incompatíveis</span><span class="sxs-lookup"><span data-stu-id="768f3-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="768f3-115">`MINOR` é incrementado quando você adiciona funcionalidades de maneira compatível com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="768f3-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="768f3-116">`PATCH` é incrementado quando você faz correções de bugs compatíveis com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="768f3-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="768f3-117">Também há maneiras de especificar outros cenários, como versões de pré-lançamento etc. ao aplicar informações de versão à sua biblioteca .NET.</span><span class="sxs-lookup"><span data-stu-id="768f3-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="768f3-118">Compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="768f3-118">Backwards Compatibility</span></span>

<span data-ttu-id="768f3-119">Conforme você lança novas versões de sua biblioteca, a compatibilidade com versões anteriores provavelmente será uma de suas principais preocupações.</span><span class="sxs-lookup"><span data-stu-id="768f3-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="768f3-120">Uma nova versão da biblioteca será compatível com a origem de uma versão anterior se o código que depende da versão anterior puder, quando recompilado, trabalhar com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="768f3-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="768f3-121">Uma nova versão da biblioteca será compatível de forma binária se um aplicativo que dependia da versão anterior puder, sem recompilação, trabalhar com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="768f3-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="768f3-122">Aqui estão algumas coisas a serem consideradas ao tentar manter a compatibilidade com versões mais antigas de sua biblioteca:</span><span class="sxs-lookup"><span data-stu-id="768f3-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="768f3-123">Métodos virtuais: Quando você transforma um método virtual em não virtual na nova versão, isso significa que os projetos que substituem esse método precisarão ser atualizados.</span><span class="sxs-lookup"><span data-stu-id="768f3-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="768f3-124">Essa é uma alteração muito grande e significativa que é altamente desaconselhável.</span><span class="sxs-lookup"><span data-stu-id="768f3-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="768f3-125">Assinaturas de método: Quando a atualização do comportamento de um método exige a alteração de sua assinatura também, você deve criar uma sobrecarga, de modo que o código que chamar esse método ainda funcione.</span><span class="sxs-lookup"><span data-stu-id="768f3-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="768f3-126">Você sempre pode manipular a assinatura de método antiga para chamar a nova assinatura de método para que a implementação permaneça consistente.</span><span class="sxs-lookup"><span data-stu-id="768f3-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="768f3-127">[Atributo obsoleto](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Use esse atributo no código para especificar classes ou membros da classe que foram preteridos e provavelmente serão removidos em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="768f3-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="768f3-128">Isso garante que os desenvolvedores que utilizam sua biblioteca estarão melhor preparados para alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="768f3-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="768f3-129">Argumentos de método opcionais: Quando você tornar argumentos de método que antes eram opcionais em obrigatórios ou alterar seu valor padrão, todo o código que não fornecer esses argumentos precisará ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="768f3-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="768f3-130">Tornar argumentos compulsórios em opcionais deve ter muito pouco efeito, especialmente se não alterar o comportamento do método.</span><span class="sxs-lookup"><span data-stu-id="768f3-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="768f3-131">Quanto mais fácil for para os usuários atualizarem para a nova versão da sua biblioteca, mais provável será que eles atualizem o quanto antes.</span><span class="sxs-lookup"><span data-stu-id="768f3-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="768f3-132">Arquivo de Configuração do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="768f3-132">Application Configuration File</span></span>

<span data-ttu-id="768f3-133">Como um desenvolvedor de .NET, há uma chance muito grande de você já ter encontrado o [arquivo o `app.config`](../framework/configure-apps/file-schema/index.md) na maioria dos tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="768f3-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="768f3-134">Esse arquivo de configuração simples pode fazer muita diferença para melhorar a distribuição de novas atualizações.</span><span class="sxs-lookup"><span data-stu-id="768f3-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="768f3-135">Em geral, você deve projetar suas bibliotecas de forma que as informações que provavelmente serão alteradas regularmente sejam armazenadas no arquivo `app.config`. Dessa forma, quando essas informações forem atualizadas, o arquivo de configuração de versões mais antigas só precisa ser substituído pelo novo, sem a necessidade de recompilar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="768f3-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="768f3-136">Consumindo bibliotecas</span><span class="sxs-lookup"><span data-stu-id="768f3-136">Consuming Libraries</span></span>

<span data-ttu-id="768f3-137">Como um desenvolvedor que consome bibliotecas .NET criadas por outros desenvolvedores, vocês provavelmente está ciente de que uma nova versão de uma biblioteca pode não ser totalmente compatível com seu projeto e pode acabar precisando atualizar seu código para trabalhar com essas alterações.</span><span class="sxs-lookup"><span data-stu-id="768f3-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="768f3-138">Para sua sorte, o ecossistema do C# e do .NET tem recursos e técnicas que permitem facilmente atualizar nosso aplicativo para trabalhar com novas versões das bibliotecas que podem introduzir alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="768f3-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="768f3-139">Redirecionamento de associação de assembly</span><span class="sxs-lookup"><span data-stu-id="768f3-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="768f3-140">Você pode usar o arquivo `app.config` para atualizar a versão de uma biblioteca que seu aplicativo usa.</span><span class="sxs-lookup"><span data-stu-id="768f3-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="768f3-141">Adicionando o que é chamado de [*redirecionamento de associação*](../framework/configure-apps/redirect-assembly-versions.md), você pode usar a nova versão da biblioteca sem precisar recompilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="768f3-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="768f3-142">O exemplo a seguir mostra como atualizar o arquivo `app.config` de seu aplicativo para uso com a versão de patch `1.0.1` do `ReferencedLibrary` em vez da versão `1.0.0` com que ele foi compilado originalmente.</span><span class="sxs-lookup"><span data-stu-id="768f3-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="768f3-143">Essa abordagem só funcionará se a nova versão do `ReferencedLibrary` for compatível de forma binária com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="768f3-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="768f3-144">Consulte a seção [Compatibilidade com versões anteriores](#backwards-compatibility) acima para ver as alterações importantes ao determinar a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="768f3-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="768f3-145">new</span><span class="sxs-lookup"><span data-stu-id="768f3-145">new</span></span>

<span data-ttu-id="768f3-146">Você usa o modificador `new` para ocultar membros herdados de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="768f3-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="768f3-147">Essa é uma maneira das classes derivadas responderem a atualizações em classes base.</span><span class="sxs-lookup"><span data-stu-id="768f3-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="768f3-148">Veja o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="768f3-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="768f3-149">**Saída**</span><span class="sxs-lookup"><span data-stu-id="768f3-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="768f3-150">No exemplo acima, você pode ver como `DerivedClass` oculta o método `MyMethod` presente em `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="768f3-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="768f3-151">Isso significa que quando uma classe base na nova versão de uma biblioteca adiciona um membro que já existe em sua classe derivada, você pode simplesmente usar o modificador `new` no membro de sua classe derivada para ocultar o membro da classe base.</span><span class="sxs-lookup"><span data-stu-id="768f3-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="768f3-152">Quando nenhum modificador `new` é especificado, uma classe derivada ocultará por padrão membros conflitantes em uma classe base e, embora um aviso do compilador seja gerado, o código ainda será compilado.</span><span class="sxs-lookup"><span data-stu-id="768f3-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="768f3-153">Isso significa que simplesmente adicionar novos membros a uma classe existente torna a nova versão da biblioteca compatível com a origem e de forma binária com o código que depende dela.</span><span class="sxs-lookup"><span data-stu-id="768f3-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="768f3-154">override</span><span class="sxs-lookup"><span data-stu-id="768f3-154">override</span></span>

<span data-ttu-id="768f3-155">O modificador `override` significa que uma implementação derivada estende a implementação de um membro da classe base, em vez de ocultá-lo.</span><span class="sxs-lookup"><span data-stu-id="768f3-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="768f3-156">O membro da classe base precisa ter o modificador `virtual` aplicado a ele.</span><span class="sxs-lookup"><span data-stu-id="768f3-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="768f3-157">**Saída**</span><span class="sxs-lookup"><span data-stu-id="768f3-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="768f3-158">O modificador `override` é avaliado em tempo de compilação e o compilador gerará um erro se não encontrar um membro virtual para substituir.</span><span class="sxs-lookup"><span data-stu-id="768f3-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="768f3-159">Seu conhecimento sobre as técnicas discutidas, bem como sua compreensão das situações em que usá-las, farão muita diferença para facilitar a transição entre versões de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="768f3-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
 