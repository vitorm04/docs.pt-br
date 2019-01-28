---
title: Alterações da falha e bibliotecas do .NET
description: Práticas recomendadas para navegar por alterações da falha ao criar bibliotecas .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: a5cfd2dfb544b2e47a87bd0939990ae73e5eda9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564218"
---
# <a name="breaking-changes"></a><span data-ttu-id="48f0c-103">Alterações da falha</span><span class="sxs-lookup"><span data-stu-id="48f0c-103">Breaking changes</span></span>

<span data-ttu-id="48f0c-104">É importante que uma biblioteca .NET encontre um equilíbrio entre a estabilidade para usuários existentes e a inovação para o futuro.</span><span class="sxs-lookup"><span data-stu-id="48f0c-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="48f0c-105">Autores de biblioteca tendem a refatorar e repensar o código até que ele fique perfeito, mas causar falhas para seus usuários existentes tem um impacto negativo, especialmente para bibliotecas de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="48f0c-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="48f0c-106">Tipos de projeto e alterações da falha</span><span class="sxs-lookup"><span data-stu-id="48f0c-106">Project types and breaking changes</span></span>

<span data-ttu-id="48f0c-107">O modo como uma biblioteca é usada pela comunidade do .NET altera o efeito das alterações de falha sobre os desenvolvedores para o usuário final.</span><span class="sxs-lookup"><span data-stu-id="48f0c-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

* <span data-ttu-id="48f0c-108">**Bibliotecas de nível médio e baixo**, tais como um serializador, analisador HTML, mapeador relacional de objeto de banco de dados ou estrutura da Web, são mais afetados por alterações da falha.</span><span class="sxs-lookup"><span data-stu-id="48f0c-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="48f0c-109">Pacotes de blocos de construção são usados tanto por desenvolvedores para o usuário final, a fim de criar aplicativos, quanto por outras bibliotecas, como dependências do NuGet.</span><span class="sxs-lookup"><span data-stu-id="48f0c-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="48f0c-110">Por exemplo, você está criando um aplicativo e usando um cliente de software livre para chamar um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="48f0c-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="48f0c-111">Uma atualização da falha para uma dependência que o cliente usa não é algo que você pode consertar.</span><span class="sxs-lookup"><span data-stu-id="48f0c-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="48f0c-112">É o cliente de software livre que precisa ser alterado e você não tem controle sobre ele.</span><span class="sxs-lookup"><span data-stu-id="48f0c-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="48f0c-113">Você precisa localizar as versões compatíveis das bibliotecas ou enviar uma correção para a biblioteca de clientes e aguardar uma nova versão.</span><span class="sxs-lookup"><span data-stu-id="48f0c-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="48f0c-114">A pior situação é quando você deseja usar duas bibliotecas que dependem de versões mutuamente incompatíveis de uma biblioteca de terceiro.</span><span class="sxs-lookup"><span data-stu-id="48f0c-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

* <span data-ttu-id="48f0c-115">**Bibliotecas de alto nível**, tais como um pacote de controles de interface do usuário, são menos sensíveis a alterações da falha.</span><span class="sxs-lookup"><span data-stu-id="48f0c-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="48f0c-116">Bibliotecas de alto nível são referenciadas diretamente em um aplicativo do usuário final.</span><span class="sxs-lookup"><span data-stu-id="48f0c-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="48f0c-117">Se ocorrerem alterações da falha, o desenvolvedor poderá optar por atualizar para a versão mais recente ou poderá modificar seu aplicativo para funcionar com a alteração da falha.</span><span class="sxs-lookup"><span data-stu-id="48f0c-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="48f0c-118">**✔️ PENSE** em como sua biblioteca será usada.</span><span class="sxs-lookup"><span data-stu-id="48f0c-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="48f0c-119">Que efeito as alterações da falha terão sobre aplicativos e bibliotecas que a usam?</span><span class="sxs-lookup"><span data-stu-id="48f0c-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="48f0c-120">**✔️ MINIMIZE** as alterações da falha ao desenvolver uma biblioteca do .NET de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="48f0c-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="48f0c-121">**✔️ CONSIDERE** a possibilidade de publicar uma nova versão significativamente diferente da biblioteca como um novo pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="48f0c-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="48f0c-122">Tipos de alterações da falha</span><span class="sxs-lookup"><span data-stu-id="48f0c-122">Types of breaking changes</span></span>

<span data-ttu-id="48f0c-123">Alterações da falha se enquadram em categorias diferentes e não são igualmente impactantes.</span><span class="sxs-lookup"><span data-stu-id="48f0c-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="48f0c-124">Alteração da falha de origem</span><span class="sxs-lookup"><span data-stu-id="48f0c-124">Source breaking change</span></span>

<span data-ttu-id="48f0c-125">Uma alteração da falha de origem não afeta a execução do programa, mas causará erros de compilação na próxima vez que o aplicativo for recompilado.</span><span class="sxs-lookup"><span data-stu-id="48f0c-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="48f0c-126">Por exemplo, uma nova sobrecarga pode criar ambiguidade em chamadas de método que antes estavam inequívocas ou um parâmetro renomeado interromperá os chamadores que usam parâmetros nomeados.</span><span class="sxs-lookup"><span data-stu-id="48f0c-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="48f0c-127">Já que uma fonte de alteração da falha só é prejudicial quando os desenvolvedores recompilam seus aplicativos, ela a alteração da falha com menos interrupções.</span><span class="sxs-lookup"><span data-stu-id="48f0c-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="48f0c-128">Os desenvolvedores podem consertar facilmente seu próprio código-fonte desfeito.</span><span class="sxs-lookup"><span data-stu-id="48f0c-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="48f0c-129">Alteração da falha de comportamento</span><span class="sxs-lookup"><span data-stu-id="48f0c-129">Behavior breaking change</span></span>

<span data-ttu-id="48f0c-130">Alterações de comportamento são o tipo mais comum de alteração da falha: quase qualquer alteração no comportamento poderia interromper alguém.</span><span class="sxs-lookup"><span data-stu-id="48f0c-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="48f0c-131">Alterações na sua biblioteca, tais como assinaturas de método, exceções geradas ou formatos de dados de entrada ou saída, podem todas afetar negativamente seus consumidores de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="48f0c-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="48f0c-132">Até mesmo uma correção de bug pode se qualificar como uma alteração da falha se os usuários contavam com o comportamento anteriormente desfeito.</span><span class="sxs-lookup"><span data-stu-id="48f0c-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="48f0c-133">Adicionar recursos e melhorar maus comportamentos são uma coisa boa, mas fazê-lo sem cuidado pode dificultar muito o processo de atualização para os usuários existentes.</span><span class="sxs-lookup"><span data-stu-id="48f0c-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="48f0c-134">Uma abordagem para ajudar os desenvolvedores a lidar com alterações da falha de comportamento é ocultá-las atrás de configurações.</span><span class="sxs-lookup"><span data-stu-id="48f0c-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="48f0c-135">As configurações permitem que os desenvolvedores atualizem para a versão mais recente da sua biblioteca, optando simultaneamente por aceitar ou recusar alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="48f0c-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="48f0c-136">Essa estratégia permite que os desenvolvedores se mantenham atualizados, permitindo ao seu código de consumo adaptar-se ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="48f0c-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="48f0c-137">Por exemplo, o ASP.NET Core MVC tem o conceito de uma [versão de compatibilidade](/aspnet/core/mvc/compatibility-version) que modifica os recursos habilitados e desabilitados em `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="48f0c-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="48f0c-138">**✔️ CONSIDERE** a possibilidade de deixar novos recursos desativados por padrão se eles afetam os usuários existentes e permitir que os desenvolvedores escolham usar o recurso com uma configuração.</span><span class="sxs-lookup"><span data-stu-id="48f0c-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="48f0c-139">Alteração da falha binária</span><span class="sxs-lookup"><span data-stu-id="48f0c-139">Binary breaking change</span></span>

<span data-ttu-id="48f0c-140">Uma alteração da falha binária acontece quando você altera a API pública de sua biblioteca, portanto, os assemblies compilados para versões mais antigas da sua biblioteca não são mais capazes de chamar a API.</span><span class="sxs-lookup"><span data-stu-id="48f0c-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="48f0c-141">Por exemplo, a alteração de assinatura de um método por meio da adição de um novo parâmetro fará com que assemblies compilados com a versão mais antiga da biblioteca lancem um <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="48f0c-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="48f0c-142">Um alteração da falha binária também pode interromper um **assembly inteiro**.</span><span class="sxs-lookup"><span data-stu-id="48f0c-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="48f0c-143">Renomear um assembly com `AssemblyName` alterará a identidade do assembly, o que também ocorrerá ao adicionar, remover ou alterar a chave de nomenclatura forte do assembly.</span><span class="sxs-lookup"><span data-stu-id="48f0c-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="48f0c-144">Uma alteração da identidade de um assembly interromperá todo o código compilado que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="48f0c-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="48f0c-145">**❌ NÃO** altere um nome de assembly.</span><span class="sxs-lookup"><span data-stu-id="48f0c-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="48f0c-146">**❌ NÃO** adicione, remova nem altere a chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="48f0c-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="48f0c-147">**✔️ CONSIDERE** a possibilidade de usar classes base abstratas em vez de interfaces.</span><span class="sxs-lookup"><span data-stu-id="48f0c-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="48f0c-148">Adicionar qualquer coisa a uma interface fará com que os tipos existentes que a implementam falhem.</span><span class="sxs-lookup"><span data-stu-id="48f0c-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="48f0c-149">Uma classe base abstrata permite que você adicione uma implementação de virtual padrão.</span><span class="sxs-lookup"><span data-stu-id="48f0c-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="48f0c-150">**✔️ CONSIDERE** a possibilidade de colocar o <xref:System.ObsoleteAttribute> nos tipos e membros que você pretende remover.</span><span class="sxs-lookup"><span data-stu-id="48f0c-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="48f0c-151">O atributo deve ter instruções para atualizar o código para não usar mais a API obsoleta.</span><span class="sxs-lookup"><span data-stu-id="48f0c-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="48f0c-152">Código que chamar tipos e métodos com o <xref:System.ObsoleteAttribute> gerará um aviso de build com a mensagem fornecida ao atributo.</span><span class="sxs-lookup"><span data-stu-id="48f0c-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="48f0c-153">Os avisos dão, às pessoas que usam a superfície de API obsoleta, tempo para migrar, de modo que quando a API obsoleta é removida, a maioria já não está a usando mais.</span><span class="sxs-lookup"><span data-stu-id="48f0c-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="48f0c-154">**✔️ CONSIDERE** a possibilidade de manter os tipos e métodos com o <xref:System.ObsoleteAttribute> indefinidamente em bibliotecas de nível médio e baixo.</span><span class="sxs-lookup"><span data-stu-id="48f0c-154">**✔️ CONSIDER** keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="48f0c-155">Remover APIs é uma alteração da falha binária.</span><span class="sxs-lookup"><span data-stu-id="48f0c-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="48f0c-156">Considere a possibilidade de manter métodos e tipos obsoletos se mantê-los tem baixo custo e não adiciona muitas dívidas técnicas à sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="48f0c-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="48f0c-157">Não remover tipos e métodos pode ajudar a evitar os piores cenários mencionados acima.</span><span class="sxs-lookup"><span data-stu-id="48f0c-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="48f0c-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48f0c-158">See also</span></span>

- [<span data-ttu-id="48f0c-159">Considerações sobre versão e atualização para os desenvolvedores de C#</span><span class="sxs-lookup"><span data-stu-id="48f0c-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="48f0c-160">Um guia definitivo para as alterações da falha de API no .NET</span><span class="sxs-lookup"><span data-stu-id="48f0c-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="48f0c-161">Regras de alteração da falha do CoreFX</span><span class="sxs-lookup"><span data-stu-id="48f0c-161">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="48f0c-162">Anterior</span><span class="sxs-lookup"><span data-stu-id="48f0c-162">Previous</span></span>](versioning.md)
