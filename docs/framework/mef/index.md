---
title: MEF (Managed Extensibility Framework)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fa91b6f2866ba2dee6963d7258fe193ce058f61
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457176"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="b8383-102">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="b8383-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="b8383-103">Este tópico fornece uma visão geral da Managed Extensibility Framework introduzida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b8383-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="b8383-104">O que é a MEF?</span><span class="sxs-lookup"><span data-stu-id="b8383-104">What is MEF?</span></span>

<span data-ttu-id="b8383-105">A Managed Extensibility Framework ou MEF é uma biblioteca para criar aplicativos leves e extensíveis.</span><span class="sxs-lookup"><span data-stu-id="b8383-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="b8383-106">Ele permite que os desenvolvedores de aplicativos descubram e usem extensões sem nenhuma configuração necessária.</span><span class="sxs-lookup"><span data-stu-id="b8383-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="b8383-107">Isso também permite aos desenvolvedores de extensão encapsular o código facilmente e evitar dependências rígidas frágeis.</span><span class="sxs-lookup"><span data-stu-id="b8383-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="b8383-108">A MEF não só permite que extensões sejam reutilizadas em aplicativos, mas também entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b8383-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="b8383-109">O problema de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="b8383-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="b8383-110">Imagine que você é arquiteto de um grande aplicativo que deve fornecer suporte para extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="b8383-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="b8383-111">Seu aplicativo deve incluir um número possivelmente grande de componentes menores, sendo responsável por sua criação e execução.</span><span class="sxs-lookup"><span data-stu-id="b8383-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="b8383-112">O método mais simples para o problema é incluem os componentes como código-fonte no seu aplicativo e chamá-los diretamente do código.</span><span class="sxs-lookup"><span data-stu-id="b8383-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="b8383-113">Isso tem várias desvantagens óbvias.</span><span class="sxs-lookup"><span data-stu-id="b8383-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="b8383-114">Mais importante delas, não é possível adicionar novos componentes sem modificar o código-fonte, uma restrição que pode ser aceitável em, por exemplo, um aplicativo Web, mas não funciona em um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="b8383-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="b8383-115">Igualmente problemático, você não terá acesso ao código-fonte dos componentes, pois eles podem ser desenvolvidos por terceiros, pelo mesmo motivo que você não pode permitir que eles acessem o seu.</span><span class="sxs-lookup"><span data-stu-id="b8383-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="b8383-116">Uma abordagem um pouco mais sofisticada seria fornecer um ponto de extensão ou interface para permitir a separação entre o aplicativo e seus componentes.</span><span class="sxs-lookup"><span data-stu-id="b8383-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="b8383-117">Com esse modelo, você pode fornecer uma interface que um componente pode implementar e uma API para habilitá-lo a interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8383-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="b8383-118">Isso resolve o problema da necessidade de acesso ao código-fonte, mas ainda traz suas próprias dificuldades.</span><span class="sxs-lookup"><span data-stu-id="b8383-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="b8383-119">Como o aplicativo não tem qualquer capacidade para descobrir componentes por conta própria, ele deve ainda ser explicitamente informado de quais componentes estão disponíveis e quais devem ser carregados.</span><span class="sxs-lookup"><span data-stu-id="b8383-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="b8383-120">Normalmente, isso é feito registrando explicitamente os componentes disponíveis em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b8383-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="b8383-121">Isso significa que garantir que os componentes estão corretos se torna um problema de manutenção, especialmente se for o usuário final e não o desenvolvedor que deverá fazer a atualização.</span><span class="sxs-lookup"><span data-stu-id="b8383-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="b8383-122">Além disso, os componentes são incapazes de se comunicar entre si, exceto por meio de canais rigidamente definidos do aplicativo em si.</span><span class="sxs-lookup"><span data-stu-id="b8383-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="b8383-123">Se o arquiteto do aplicativo não tiver previsto a necessidade de uma comunicação específica, ela geralmente será impossível.</span><span class="sxs-lookup"><span data-stu-id="b8383-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="b8383-124">Por fim, os desenvolvedores de componentes devem aceitar uma dependência forte no assembly que contém a interface implementada.</span><span class="sxs-lookup"><span data-stu-id="b8383-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="b8383-125">Isso torna difícil para um componente a ser usado em mais de um aplicativo e também pode criar problemas quando você cria uma estrutura de testes para componentes.</span><span class="sxs-lookup"><span data-stu-id="b8383-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="b8383-126">O que o MEF oferece</span><span class="sxs-lookup"><span data-stu-id="b8383-126">What MEF Provides</span></span>
 <span data-ttu-id="b8383-127">Em vez desse registro explícito de componentes disponíveis, o MEF oferece uma maneira de descobri-los implicitamente, através de *composição*.</span><span class="sxs-lookup"><span data-stu-id="b8383-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="b8383-128">Um componente do MEF, chamado de *peça*, especifica declarativamente ambas as suas dependências (conhecidas como *importações*) e quais recursos (conhecidos como *exportações*) ele disponibiliza.</span><span class="sxs-lookup"><span data-stu-id="b8383-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="b8383-129">Quando uma peça é criada, o mecanismo de composição do MEF atende às suas importações com o que está disponível de outras peças.</span><span class="sxs-lookup"><span data-stu-id="b8383-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="b8383-130">Essa abordagem resolve os problemas abordados na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b8383-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="b8383-131">Como as peças do MEF especificam de forma declarativa seus recursos, elas são descobertas no tempo de execução, o que significa que um aplicativo usar as peças embutidas em código sem referências ou arquivos de configuração frágeis.</span><span class="sxs-lookup"><span data-stu-id="b8383-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="b8383-132">O MEF permite que os aplicativos descubram e examinem as peças por seus metadados, sem instanciá-las ou até mesmo carregar seus assemblies.</span><span class="sxs-lookup"><span data-stu-id="b8383-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="b8383-133">Como resultado, não é necessário especificar cuidadosamente quando e como as extensões devem ser carregadas.</span><span class="sxs-lookup"><span data-stu-id="b8383-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="b8383-134">Além de suas exportações fornecidas, uma peça pode especificar suas importações, será preenchida por outras peças.</span><span class="sxs-lookup"><span data-stu-id="b8383-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="b8383-135">Isso não somente torna a comunicação entre peças possível, mas muito mais fácil, e permite faturamento correto do código.</span><span class="sxs-lookup"><span data-stu-id="b8383-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="b8383-136">Por exemplo, serviços comuns a muitos componentes podem ser faturados em uma peça separada e facilmente modificados ou substituídos.</span><span class="sxs-lookup"><span data-stu-id="b8383-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="b8383-137">Como o modelo de MEF não exige nenhuma dependência em um assembly de aplicativo específico, ele permite que extensões sejam reusadas de aplicativo para aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8383-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="b8383-138">Isso também facilita desenvolver um agente de teste, independente do aplicativo, para testar os componentes de extensão.</span><span class="sxs-lookup"><span data-stu-id="b8383-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="b8383-139">Um aplicativo extensível escrito com o MEF declara uma importação que pode ser preenchida por componentes de extensão e também pode declarar exportações para expor serviços de aplicativo para extensões.</span><span class="sxs-lookup"><span data-stu-id="b8383-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="b8383-140">Cada componente de extensão declara uma exportação e também pode declarar importações.</span><span class="sxs-lookup"><span data-stu-id="b8383-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="b8383-141">Dessa forma, os próprios componentes de extensão são automaticamente extensíveis.</span><span class="sxs-lookup"><span data-stu-id="b8383-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="b8383-142">Onde o MEF está disponível?</span><span class="sxs-lookup"><span data-stu-id="b8383-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="b8383-143">O MEF é parte integrante do .NET Framework 4 e está disponível em qualquer lugar em que o .NET Framework é usado.</span><span class="sxs-lookup"><span data-stu-id="b8383-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="b8383-144">Você pode usar o MEF em seus aplicativos clientes, seja usando o Windows Forms, WPF ou qualquer outra tecnologia ou em aplicativos de servidores que usam o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b8383-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="b8383-145">MEF e MAF</span><span class="sxs-lookup"><span data-stu-id="b8383-145">MEF and MAF</span></span>
 <span data-ttu-id="b8383-146">Versões anteriores do .NET Framework introduziram o MAF (Managed Add-in Framework), projetado para permitir que aplicativos isolem e gerenciem extensões.</span><span class="sxs-lookup"><span data-stu-id="b8383-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="b8383-147">O foco do MAF é em um nível ligeiramente mais elevado que o MEF, concentrando-se no isolamento de extensão e carregamento e descarregamento do assembly, enquanto o foco do MEF é a descoberta, extensibilidade e portabilidade.</span><span class="sxs-lookup"><span data-stu-id="b8383-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="b8383-148">As duas estruturas interoperam sem problemas entre si e um único aplicativo pode aproveitar ambas.</span><span class="sxs-lookup"><span data-stu-id="b8383-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="b8383-149">SimpleCalculator: Um aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="b8383-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="b8383-150">A maneira mais simples de ver o que o MEF é criar um aplicativo MEF simples.</span><span class="sxs-lookup"><span data-stu-id="b8383-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="b8383-151">Neste exemplo, você criará uma calculadora muito simples chamada SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="b8383-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="b8383-152">A meta da SimpleCalculator é criar um aplicativo de console que aceite comandos aritméticos básicos, no formato "5+3" ou "6-2" e retorne as respostas corretas.</span><span class="sxs-lookup"><span data-stu-id="b8383-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="b8383-153">Usando MEF, você poderá adicionar novos operadores sem alterar o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8383-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="b8383-154">Para baixar o código completo deste exemplo, confira o [exemplo SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="b8383-154">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="b8383-155">A finalidade da SimpleCalculator é demonstrar os conceitos e a sintaxe do MEF, em vez de fornecer necessariamente um cenário realista para seu uso.</span><span class="sxs-lookup"><span data-stu-id="b8383-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="b8383-156">Muitos dos aplicativos que mais se beneficiariam da potência do MEF são mais complexos que a SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="b8383-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="b8383-157">Para obter exemplos mais abrangentes, confira o [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="b8383-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="b8383-158">Para começar, no Visual Studio, crie um novo projeto de aplicativo de Console e dê a ele o nome `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="b8383-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="b8383-159">Adicione uma referência ao assembly System.ComponentModel.Composition, no qual reside o MEF.</span><span class="sxs-lookup"><span data-stu-id="b8383-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="b8383-160">Abra o Module1.vb ou o Program.cs e adicione as instruções `Imports` ou `using` System.ComponentModel.Composition e System.ComponentModel.Composition.Hosting.</span><span class="sxs-lookup"><span data-stu-id="b8383-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="b8383-161">Esses dois namespaces contêm tipos MEF que você precisará para desenvolver um aplicativo extensível.</span><span class="sxs-lookup"><span data-stu-id="b8383-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="b8383-162">Se você estiver usando o Visual Basic, adicione a palavra-chave `Public` à linha que declara o módulo `Module1`.</span><span class="sxs-lookup"><span data-stu-id="b8383-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="b8383-163">Catálogos e contêiner de composição</span><span class="sxs-lookup"><span data-stu-id="b8383-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="b8383-164">O núcleo do modelo de composição de MEF é o *contêiner de composição*, que contém todas as peças disponíveis e executa a composição.</span><span class="sxs-lookup"><span data-stu-id="b8383-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="b8383-165">Composição e a correspondência de importações e exportações.</span><span class="sxs-lookup"><span data-stu-id="b8383-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="b8383-166">O tipo mais comum de contêiner de composição é <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, e você o usará na SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="b8383-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="b8383-167">Se você estiver usando o Visual Basic, Module1, adicione uma classe pública denominada `Program`.</span><span class="sxs-lookup"><span data-stu-id="b8383-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="b8383-168">Adicione a seguinte linha para à classe `Program` no Module1 ou Program.cs:</span><span class="sxs-lookup"><span data-stu-id="b8383-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="b8383-169">Para descobrir as peças disponíveis para ele, os contêineres de composição usam um *catálogo*.</span><span class="sxs-lookup"><span data-stu-id="b8383-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="b8383-170">Um catálogo é um objeto que disponibiliza as peças descobertas em alguma origem.</span><span class="sxs-lookup"><span data-stu-id="b8383-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="b8383-171">O MEF fornece catálogos para descobrir peças de um tipo fornecido, um assembly ou de um diretório.</span><span class="sxs-lookup"><span data-stu-id="b8383-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="b8383-172">Os desenvolvedores de aplicativos podem criar facilmente novos catálogos para descobrir as peças de outras fontes, como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b8383-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="b8383-173">Adicione o seguinte construtor à classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="b8383-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="b8383-174">A chamada para <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> instrui o contêiner de composição a compor um conjunto específico de peças, neste caso a instância atual do `Program`.</span><span class="sxs-lookup"><span data-stu-id="b8383-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="b8383-175">Neste ponto, no entanto, nada acontecerá, pois o `Program` tem não importações a preencher.</span><span class="sxs-lookup"><span data-stu-id="b8383-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="b8383-176">Importações e exportações com atributos</span><span class="sxs-lookup"><span data-stu-id="b8383-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="b8383-177">Primeiro, o `Program` importa uma calculadora.</span><span class="sxs-lookup"><span data-stu-id="b8383-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="b8383-178">Isso separa questões de interface do usuário, tal como a entrada e a saída do console que entrará em `Program`, da lógica da calculadora.</span><span class="sxs-lookup"><span data-stu-id="b8383-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="b8383-179">Adicione o seguinte código à classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="b8383-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="b8383-180">Observe que a declaração do objeto `calculator` não é incomum, mas sim que está decorada com o atributo <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b8383-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="b8383-181">Esse atributo declara algo como uma importação; ou seja, ele será preenchido pelo mecanismo de composição quando o objeto for composto.</span><span class="sxs-lookup"><span data-stu-id="b8383-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="b8383-182">Cada importação tem um *contrato*, que determina com quais exportações ele corresponderá.</span><span class="sxs-lookup"><span data-stu-id="b8383-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="b8383-183">O contrato pode ser uma cadeia de caracteres especificada explicitamente ou ele pode ser automaticamente gerado pelo MEF por meio de um determinado tipo, neste caso, a interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="b8383-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="b8383-184">Qualquer exportação declarada com um contrato correspondente atender a esta importação.</span><span class="sxs-lookup"><span data-stu-id="b8383-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="b8383-185">Observe que, enquanto o tipo do objeto `calculator` é na verdade `ICalculator`, isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="b8383-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="b8383-186">O contrato é independente do tipo do objeto de importação.</span><span class="sxs-lookup"><span data-stu-id="b8383-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="b8383-187">(Nesse caso, você poderia deixar o `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="b8383-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="b8383-188">O MEF automaticamente assumirá que o contrato se baseia no tipo da importação, a menos que seja especificado explicitamente.)</span><span class="sxs-lookup"><span data-stu-id="b8383-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="b8383-189">Adicione essa interface simples ao módulo ou ao namespace `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 <span data-ttu-id="b8383-190">Agora que você definiu o `ICalculator`, precisará de uma classe que o implemente.</span><span class="sxs-lookup"><span data-stu-id="b8383-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="b8383-191">Adicione a seguinte classe ao módulo ou ao namespace `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

 <span data-ttu-id="b8383-192">Aqui está a exportação que corresponde à importação em `Program`.</span><span class="sxs-lookup"><span data-stu-id="b8383-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="b8383-193">Para que a exportação corresponda à importação, a exportação deverá ter o mesmo contrato.</span><span class="sxs-lookup"><span data-stu-id="b8383-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="b8383-194">Exportando sob um contrato com base em `typeof(MySimpleCalculator)` produziria uma incompatibilidade e a importação não seria preenchida. O contrato deve ter correspondência exata.</span><span class="sxs-lookup"><span data-stu-id="b8383-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="b8383-195">Uma vez que o contêiner de composição será populado com todas as peças disponíveis nesse assembly, a peça `MySimpleCalculator` estará disponível.</span><span class="sxs-lookup"><span data-stu-id="b8383-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="b8383-196">Quando o construtor do `Program` executa a composição do objeto `Program`, sua importação será preenchida por um objeto `MySimpleCalculator`, que será criado para este fim.</span><span class="sxs-lookup"><span data-stu-id="b8383-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="b8383-197">A camada de interface do usuário (`Program`) não precisa saber de mais nada.</span><span class="sxs-lookup"><span data-stu-id="b8383-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="b8383-198">Portanto, você pode preencher o resto da lógica de interface do usuário no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="b8383-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="b8383-199">Adicione o seguinte código ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="b8383-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="b8383-200">Esse código simplesmente lê uma linha de entrada e chama a função `Calculate` do `ICalculator` no resultado, que ele grava de volta ao console.</span><span class="sxs-lookup"><span data-stu-id="b8383-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="b8383-201">Este é todo o código necessário no `Program`.</span><span class="sxs-lookup"><span data-stu-id="b8383-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="b8383-202">Todo o resto do trabalho ocorrerá nas peças.</span><span class="sxs-lookup"><span data-stu-id="b8383-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="b8383-203">Outras Importações e ImportMany</span><span class="sxs-lookup"><span data-stu-id="b8383-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="b8383-204">Para que a SimpleCalculator seja extensível, ela precisa importar uma lista de operações.</span><span class="sxs-lookup"><span data-stu-id="b8383-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="b8383-205">Um atributo <xref:System.ComponentModel.Composition.ImportAttribute> ordinário é preenchido por um e somente um <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b8383-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="b8383-206">Se houver mais de uma disponível, o mecanismo de composição gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="b8383-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="b8383-207">Para criar uma importação pode ser preenchida por qualquer número de exportações, você pode usar o atributo <xref:System.ComponentModel.Composition.ImportManyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b8383-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="b8383-208">Adicione as seguintes propriedades de operações à classe `MySimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="b8383-209"><xref:System.Lazy%602> é um tipo é fornecido pelo MEF para manter indiretas referências a exportações.</span><span class="sxs-lookup"><span data-stu-id="b8383-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="b8383-210">Aqui, além do próprio objeto exportado, você também obtém os *metadados da exportação* ou informações que descrevem o objeto exportado.</span><span class="sxs-lookup"><span data-stu-id="b8383-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="b8383-211">Cada <xref:System.Lazy%602> contém um objeto `IOperation`, que representa uma operação real, e um objeto `IOperationData`, que representa seus metadados.</span><span class="sxs-lookup"><span data-stu-id="b8383-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="b8383-212">Adicione as interfaces simples a seguir ao módulo ou ao namespace `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="b8383-213">Nesse caso, os metadados para cada operação são o símbolo que representa a operação, como +, -, \*, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b8383-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="b8383-214">Para disponibilizar a operação de adição, adicione a seguinte classe ao módulo ou ao namespace `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

 <span data-ttu-id="b8383-215">O atributo <xref:System.ComponentModel.Composition.ExportAttribute> funciona como antes.</span><span class="sxs-lookup"><span data-stu-id="b8383-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="b8383-216">O atributo <xref:System.ComponentModel.Composition.ExportMetadataAttribute> anexa metadados na forma de um par de nome-valor à exportação.</span><span class="sxs-lookup"><span data-stu-id="b8383-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="b8383-217">Enquanto a classe `Add` implementa `IOperation`, uma classe que implementa `IOperationData` não é definida explicitamente.</span><span class="sxs-lookup"><span data-stu-id="b8383-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="b8383-218">Em vez disso, uma classe é implicitamente criada pelo MEF com propriedades baseadas nos nomes dos metadados fornecidos.</span><span class="sxs-lookup"><span data-stu-id="b8383-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="b8383-219">(Isso é uma das várias maneiras de acessar os metadados no MEF.)</span><span class="sxs-lookup"><span data-stu-id="b8383-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="b8383-220">A composição no MEF é *recursiva*.</span><span class="sxs-lookup"><span data-stu-id="b8383-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="b8383-221">Você compõe explicitamente o objeto `Program`, que importou um `ICalculator` que acabou sendo do tipo `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="b8383-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="b8383-222">O `MySimpleCalculator`, por sua vez, importa um conjunto de objetos `IOperation` e essa importação será preenchida quando `MySimpleCalculator` é criado, ao mesmo tempo que as importações do `Program`.</span><span class="sxs-lookup"><span data-stu-id="b8383-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="b8383-223">Se a classe `Add` declarar outra importação, ela também deverá ser preenchida, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b8383-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="b8383-224">Quaisquer importações não preenchidas resultam em um erro de composição.</span><span class="sxs-lookup"><span data-stu-id="b8383-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="b8383-225">(É possível, no entanto, declarar importações como opcional ou atribuir valores padrão.)</span><span class="sxs-lookup"><span data-stu-id="b8383-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="b8383-226">Lógica da Calculadora</span><span class="sxs-lookup"><span data-stu-id="b8383-226">Calculator Logic</span></span>
 <span data-ttu-id="b8383-227">Com as peças no lugar, falta apenas a própria lógica da calculadora.</span><span class="sxs-lookup"><span data-stu-id="b8383-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="b8383-228">Adicione o seguinte código na classe `MySimpleCalculator` para implementar o método `Calculate`:</span><span class="sxs-lookup"><span data-stu-id="b8383-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(String input)
{
    int left;
    int right;
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

 <span data-ttu-id="b8383-229">As etapas iniciais analisam a cadeia de caracteres de entrada em operandos esquerdo e direito e um caractere de operador.</span><span class="sxs-lookup"><span data-stu-id="b8383-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="b8383-230">No loop `foreach`, cada membro da coleção `operations` é examinado.</span><span class="sxs-lookup"><span data-stu-id="b8383-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="b8383-231">Esses objetos são do tipo <xref:System.Lazy%602> e seus valores de metadados e o objeto exportado o podem ser acessados com as propriedades <xref:System.Lazy%602.Metadata%2A> e <xref:System.Lazy%601.Value%2A>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b8383-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="b8383-232">Nesse caso, se a propriedade `Symbol` do objeto `IOperationData` for correspondente, a calculadora chamará o método `Operate` do objeto `IOperation` e retornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="b8383-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="b8383-233">Para concluir a calculadora, também é necessário um método auxiliar que retorna a posição do primeiro caractere não dígito em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8383-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="b8383-234">Adicione o seguinte método auxiliar para a classe `MySimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="b8383-235">Agora você poderá compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="b8383-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="b8383-236">No Visual Basic, certifique-se de adicionar a palavra-chave `Public` ao `Module1`.</span><span class="sxs-lookup"><span data-stu-id="b8383-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="b8383-237">Na janela do console, digite uma operação de adição, como "5+3", e a calculadora retorna os resultados.</span><span class="sxs-lookup"><span data-stu-id="b8383-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="b8383-238">Qualquer outro operador resulta na mensagem "Operação Não Encontrada!"</span><span class="sxs-lookup"><span data-stu-id="b8383-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="b8383-239">.</span><span class="sxs-lookup"><span data-stu-id="b8383-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="b8383-240">Estendendo a SimpleCalculator usando uma nova classe</span><span class="sxs-lookup"><span data-stu-id="b8383-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="b8383-241">Agora que a calculadora funciona, adicionar uma nova operação é muito fácil.</span><span class="sxs-lookup"><span data-stu-id="b8383-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="b8383-242">Adicione a seguinte classe ao módulo ou ao namespace `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="b8383-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

 <span data-ttu-id="b8383-243">Compile e execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="b8383-243">Compile and run the project.</span></span> <span data-ttu-id="b8383-244">Digite uma operação de subtração, como "5-3".</span><span class="sxs-lookup"><span data-stu-id="b8383-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="b8383-245">A calculadora agora dá suporte à subtração, além da adição.</span><span class="sxs-lookup"><span data-stu-id="b8383-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="b8383-246">Estendendo a SimpleCalculator usando um novo assembly</span><span class="sxs-lookup"><span data-stu-id="b8383-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="b8383-247">Adicionar classes ao código-fonte é bastante simples, mas o MEF oferece a capacidade de procurar peças fora de uma fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8383-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="b8383-248">Para demonstrar isso, você precisará modificar a SimpleCalculator para pesquisar um diretório, bem como seu próprio assembly, por peças, adicionando um <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="b8383-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="b8383-249">Adicione um novo diretório chamado `Extensions` ao projeto da SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="b8383-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="b8383-250">Certifique-se de adicioná-lo no nível do projeto e não no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="b8383-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="b8383-251">Em seguida, adicione um novo projeto de Biblioteca de Classes à solução, chamado `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="b8383-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="b8383-252">O novo projeto será compilado em um assembly separado.</span><span class="sxs-lookup"><span data-stu-id="b8383-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="b8383-253">Abra o Designer de Propriedades de Projeto para o projeto ExtendedOperations e clique na guia **Compilar** ou **Criar**. Alterar o **Caminho de saída do build** ou o **Caminho de saída** para apontar para o diretório Extensions no diretório do projeto da SimpleCalculator (..\SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="b8383-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="b8383-254">No Module1.vb ou Program.cs, adicione a seguinte linha ao construtor `Program`:</span><span class="sxs-lookup"><span data-stu-id="b8383-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="b8383-255">Substitua o caminho de exemplo pelo caminho para o diretório de Extensions.</span><span class="sxs-lookup"><span data-stu-id="b8383-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="b8383-256">(Esse caminho absoluto destina-se apenas a fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="b8383-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="b8383-257">Em um aplicativo de produção, você deve usar um caminho relativo.) O <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> agora adicionará as peças encontradas a quaisquer assemblies do diretório Extensions ao contêiner de composição.</span><span class="sxs-lookup"><span data-stu-id="b8383-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="b8383-258">No projeto ExtendedOperations, adicione referências à SimpleCalculator e ao System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="b8383-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="b8383-259">No arquivo de classe ExtendedOperations, adicione um `Imports` ou uma instrução `using` para o System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="b8383-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="b8383-260">No Visual Basic, adicione também uma instrução `Imports` para a SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="b8383-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="b8383-261">Em seguida, adicione a seguinte classe ao arquivo da classe ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="b8383-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

 <span data-ttu-id="b8383-262">Observe que para o contrato corresponder, o atributo <xref:System.ComponentModel.Composition.ExportAttribute> deve ter o mesmo tipo de <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b8383-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="b8383-263">Compile e execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="b8383-263">Compile and run the project.</span></span> <span data-ttu-id="b8383-264">Teste o novo operador Mod (%).</span><span class="sxs-lookup"><span data-stu-id="b8383-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="b8383-265">Conclusão</span><span class="sxs-lookup"><span data-stu-id="b8383-265">Conclusion</span></span>
 <span data-ttu-id="b8383-266">Este tópico abordou os conceitos básicos do MEF.</span><span class="sxs-lookup"><span data-stu-id="b8383-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="b8383-267">Peças, catálogos e o contêiner de composição</span><span class="sxs-lookup"><span data-stu-id="b8383-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="b8383-268">Peças e o contêiner de composição são pilares essenciais de um aplicativo MEF.</span><span class="sxs-lookup"><span data-stu-id="b8383-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="b8383-269">Uma peça é qualquer objeto que importa ou exporta um valor, até e incluindo a si mesmo.</span><span class="sxs-lookup"><span data-stu-id="b8383-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="b8383-270">Um catálogo fornece um conjunto de peças de uma fonte específica.</span><span class="sxs-lookup"><span data-stu-id="b8383-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="b8383-271">O contêiner de composição usa as peças fornecidas por um catálogo para executar a composição, a associação de importações a exportações.</span><span class="sxs-lookup"><span data-stu-id="b8383-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="b8383-272">Importações e exportações</span><span class="sxs-lookup"><span data-stu-id="b8383-272">Imports and exports</span></span>

     <span data-ttu-id="b8383-273">Importações e exportações são o modo pelo qual os componentes se comunicam.</span><span class="sxs-lookup"><span data-stu-id="b8383-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="b8383-274">Com uma importação, o componente especifica uma necessidade por um determinado valor ou objeto e com uma exportação ele especifica a disponibilidade de um valor.</span><span class="sxs-lookup"><span data-stu-id="b8383-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="b8383-275">Cada importação é compatível com uma lista dos exportações por meio do seu contrato.</span><span class="sxs-lookup"><span data-stu-id="b8383-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="b8383-276">Para onde devo ir agora?</span><span class="sxs-lookup"><span data-stu-id="b8383-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="b8383-277">Para baixar o código completo deste exemplo, confira o [exemplo SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="b8383-277">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="b8383-278">Para obter mais informações e exemplos de código, confira [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="b8383-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="b8383-279">Para obter uma lista dos tipos de MEF, confira o namespace <xref:System.ComponentModel.Composition?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8383-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
