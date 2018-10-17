---
title: Alterações significativas e bibliotecas do .NET
description: Práticas recomendadas para navegar em alterações significativas ao criar bibliotecas .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 83c01fdad7d836877bf692b87eeb0230219ded36
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369681"
---
# <a name="breaking-changes"></a><span data-ttu-id="7b601-103">Alterações significativas</span><span class="sxs-lookup"><span data-stu-id="7b601-103">Breaking changes</span></span>

<span data-ttu-id="7b601-104">É importante para uma biblioteca .NET encontrar um equilíbrio entre a estabilidade para usuários existentes e a inovação para o futuro.</span><span class="sxs-lookup"><span data-stu-id="7b601-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="7b601-105">Autores de biblioteca de lean na direção de refatoração e repensar o código até que ele é perfeito, mas quebra a seus usuários existentes tem um impacto negativo, especialmente para bibliotecas de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="7b601-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="7b601-106">Tipos de projeto e as alterações recentes</span><span class="sxs-lookup"><span data-stu-id="7b601-106">Project types and breaking changes</span></span>

<span data-ttu-id="7b601-107">Como uma biblioteca é usada pela comunidade .NET altera o efeito das alterações significativas nos desenvolvedores do usuário final.</span><span class="sxs-lookup"><span data-stu-id="7b601-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

* <span data-ttu-id="7b601-108">**Bibliotecas de nível médio e baixo** como um serializador, analisador HTML, mapeador relacional de objeto de banco de dados ou estrutura da web são mais afetados por alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="7b601-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="7b601-109">Bloco de construção de pacotes são usados por desenvolvedores do usuário final para criar aplicativos e por outras bibliotecas como dependências do NuGet.</span><span class="sxs-lookup"><span data-stu-id="7b601-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="7b601-110">Por exemplo, você estiver criando um aplicativo e estiver usando um cliente de software livre para chamar um serviço web.</span><span class="sxs-lookup"><span data-stu-id="7b601-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="7b601-111">Uma atualização significativa para uma dependência que o cliente usa não é algo que você pode corrigir.</span><span class="sxs-lookup"><span data-stu-id="7b601-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="7b601-112">É o cliente de software livre que precisa ser alterado e você não tem controle sobre ele.</span><span class="sxs-lookup"><span data-stu-id="7b601-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="7b601-113">Você precisa localizar as versões compatíveis das bibliotecas ou enviar uma correção para a biblioteca de cliente e aguarde até que uma nova versão.</span><span class="sxs-lookup"><span data-stu-id="7b601-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="7b601-114">A pior situação é se você deseja usar duas bibliotecas que dependem de versões mutuamente incompatíveis de uma biblioteca de terceiro.</span><span class="sxs-lookup"><span data-stu-id="7b601-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

* <span data-ttu-id="7b601-115">**Bibliotecas de alto nível** como um pacote de interface do usuário controles são menos sensíveis a alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="7b601-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="7b601-116">Bibliotecas de alto nível são referenciadas diretamente em um aplicativo do usuário final.</span><span class="sxs-lookup"><span data-stu-id="7b601-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="7b601-117">Se ocorrerem alterações significativas, o desenvolvedor pode optar por atualizar para a versão mais recente, ou pode modificar seu aplicativo para trabalhar com a alteração significativa.</span><span class="sxs-lookup"><span data-stu-id="7b601-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="7b601-118">**FAZER ✔️** pense em como sua biblioteca será usada.</span><span class="sxs-lookup"><span data-stu-id="7b601-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="7b601-119">Efeito de alterações significativas terão em aplicativos e bibliotecas que usá-lo?</span><span class="sxs-lookup"><span data-stu-id="7b601-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="7b601-120">**FAZER ✔️** minimizar alterações significativas ao desenvolver uma biblioteca .NET de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="7b601-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="7b601-121">**Considere a possibilidade de ✔️** publicando um principal de reconfiguração de uma biblioteca como um novo pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="7b601-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="7b601-122">Tipos de alterações significativas</span><span class="sxs-lookup"><span data-stu-id="7b601-122">Types of breaking changes</span></span>

<span data-ttu-id="7b601-123">Alterações interruptivas se enquadram nas categorias diferentes e não são igualmente impactantes.</span><span class="sxs-lookup"><span data-stu-id="7b601-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="7b601-124">Alteração significativa de código-fonte</span><span class="sxs-lookup"><span data-stu-id="7b601-124">Source breaking change</span></span>

<span data-ttu-id="7b601-125">Uma alteração significativa de fonte não afeta a execução do programa, mas causará erros de compilação na próxima vez que o aplicativo for recompilado.</span><span class="sxs-lookup"><span data-stu-id="7b601-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="7b601-126">Por exemplo, uma nova sobrecarga pode criar ambiguidade em chamadas de método que antes estavam inequívocas, ou um parâmetro renomeado interromperá os chamadores que usam parâmetros nomeados.</span><span class="sxs-lookup"><span data-stu-id="7b601-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="7b601-127">Como uma fonte de alteração significativa é prejudicial somente quando os desenvolvedores recompilar seus aplicativos, é a alteração significativa com menos interrupções.</span><span class="sxs-lookup"><span data-stu-id="7b601-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="7b601-128">Os desenvolvedores podem corrigir facilmente seu próprio código de origem quebrado.</span><span class="sxs-lookup"><span data-stu-id="7b601-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="7b601-129">Alteração de comportamento de quebra</span><span class="sxs-lookup"><span data-stu-id="7b601-129">Behavior breaking change</span></span>

<span data-ttu-id="7b601-130">Alterações de comportamento são o tipo mais comum de alteração interruptiva: quase qualquer alteração no comportamento poderia interromper alguém.</span><span class="sxs-lookup"><span data-stu-id="7b601-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="7b601-131">Alterações na sua biblioteca, como assinaturas de método, as exceções geradas ou entrada ou saída formatos de dados, todos os pode afetar negativamente seus consumidores de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7b601-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="7b601-132">Até mesmo uma correção de bug pode se qualificar como uma alteração significativa se os usuários contavam com o comportamento desfeito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7b601-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="7b601-133">Adicionando recursos e melhorando a maus comportamentos são uma coisa boa, mas sem cuidado ele pode facilitar muito difícil para os usuários existentes para atualizar.</span><span class="sxs-lookup"><span data-stu-id="7b601-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="7b601-134">Uma abordagem para ajudar os desenvolvedores a lidar com alterações significativas de comportamento é para ocultá-los por trás de configurações.</span><span class="sxs-lookup"><span data-stu-id="7b601-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="7b601-135">As configurações permitem que os desenvolvedores a atualizar para a versão mais recente da sua biblioteca enquanto ao mesmo tempo optando por aceitar ou recusar alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="7b601-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="7b601-136">Essa estratégia permite que os desenvolvedores a se manter atualizado, permitindo que seu código de consumo adaptar-se ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="7b601-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="7b601-137">Por exemplo, o ASP.NET Core MVC tem o conceito de um [versão de compatibilidade](/aspnet/core/mvc/compatibility-version) que modifica os recursos habilitados e desabilitados em `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="7b601-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="7b601-138">**Considere a possibilidade de ✔️** omitindo novos recursos por padrão, se eles afetam os usuários existentes e permitir que os desenvolvedores a aceitar o recurso com uma configuração.</span><span class="sxs-lookup"><span data-stu-id="7b601-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="7b601-139">Alteração significativa binário</span><span class="sxs-lookup"><span data-stu-id="7b601-139">Binary breaking change</span></span>

<span data-ttu-id="7b601-140">Um binário alteração significativa acontece quando você altera a API pública de sua biblioteca, portanto, os assemblies compilados em relação a versões mais antigas da sua biblioteca não são mais capazes de chamar a API.</span><span class="sxs-lookup"><span data-stu-id="7b601-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="7b601-141">Por exemplo, a alteração de assinatura de um método, adicionando um novo parâmetro fará com que assemblies compilados com a versão mais antiga da biblioteca lançar um <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="7b601-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="7b601-142">Um alteração significativa de binário também pode interromper uma **assembly inteiro**.</span><span class="sxs-lookup"><span data-stu-id="7b601-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="7b601-143">Renomeando um assembly com `AssemblyName` alterará a identidade do assembly, assim como adicionar, remover ou alterar a chave de nomenclatura forte do assembly.</span><span class="sxs-lookup"><span data-stu-id="7b601-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="7b601-144">Uma alteração de identidade de um assembly interromperá todo o código compilado que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="7b601-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="7b601-145">**❌ NÃO** alterar um nome de assembly.</span><span class="sxs-lookup"><span data-stu-id="7b601-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="7b601-146">**❌ NÃO** adicionar, remover ou alterar a chave de nomeação forte.</span><span class="sxs-lookup"><span data-stu-id="7b601-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="7b601-147">**Considere a possibilidade de ✔️** usando classes base abstratas, em vez de interfaces.</span><span class="sxs-lookup"><span data-stu-id="7b601-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="7b601-148">Adicionar algo para uma interface fará com que os tipos existentes que implementam a falha.</span><span class="sxs-lookup"><span data-stu-id="7b601-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="7b601-149">Uma classe base abstrata permite que você adicione uma implementação de virtual padrão.</span><span class="sxs-lookup"><span data-stu-id="7b601-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="7b601-150">**Considere a possibilidade de ✔️** colocando o <xref:System.ObsoleteAttribute> nos tipos e membros que você pretende remover.</span><span class="sxs-lookup"><span data-stu-id="7b601-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="7b601-151">O atributo deve ter instruções para atualizar o código não for mais usar a API obsoleta.</span><span class="sxs-lookup"><span data-stu-id="7b601-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="7b601-152">Código que chama os tipos e métodos com o <xref:System.ObsoleteAttribute> gerará um aviso de compilação com a mensagem fornecida para o atributo.</span><span class="sxs-lookup"><span data-stu-id="7b601-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="7b601-153">As avisos oferecem as pessoas que usam o tempo de superfície de API obsoleto para migrar para que quando a API obsoleta é removida, a maioria não é mais usá-lo.</span><span class="sxs-lookup"><span data-stu-id="7b601-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

## <a name="see-also"></a><span data-ttu-id="7b601-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b601-154">See also</span></span>

* [<span data-ttu-id="7b601-155">Considerações sobre versão e atualização para os desenvolvedores de c#</span><span class="sxs-lookup"><span data-stu-id="7b601-155">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
* [<span data-ttu-id="7b601-156">Um guia definitivo para as alterações recentes de API do .NET</span><span class="sxs-lookup"><span data-stu-id="7b601-156">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [<span data-ttu-id="7b601-157">Regras de alteração de quebra do CoreFX</span><span class="sxs-lookup"><span data-stu-id="7b601-157">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[<span data-ttu-id="7b601-158">Anterior</span><span class="sxs-lookup"><span data-stu-id="7b601-158">Previous</span></span>](./versioning.md)
