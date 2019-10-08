---
title: Crie componentes de interface do usuário reutilizáveis com mais utilidade
description: Saiba como criar componentes de interface do usuário reutilizáveis com mais e como eles se comparam aos controles de Web Forms de ASP.NET.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: c9fb9b3ff59986ebaf64ecb19277ffbbc8696fed
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031799"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="9b3ff-103">Crie componentes de interface do usuário reutilizáveis com mais utilidade</span><span class="sxs-lookup"><span data-stu-id="9b3ff-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9b3ff-104">Uma das belas coisas sobre o ASP.NET Web Forms é como ela permite o encapsulamento de partes reutilizáveis do código da interface do usuário em controles de interface de usuários reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="9b3ff-105">Os controles de usuário personalizados podem ser definidos na marcação usando arquivos *. ascx* .</span><span class="sxs-lookup"><span data-stu-id="9b3ff-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="9b3ff-106">Você também pode criar controles de servidor elaborados em código com suporte completo ao designer.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="9b3ff-107">Também dá suporte ao encapsulamento de interface do usuário por meio de *componentes*.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="9b3ff-108">Um componente:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-108">A component:</span></span>

* <span data-ttu-id="9b3ff-109">É uma parte independente da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-109">Is a self-contained chunk of UI.</span></span>
* <span data-ttu-id="9b3ff-110">Mantém seu próprio Estado e lógica de renderização.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-110">Maintains its own state and rendering logic.</span></span>
* <span data-ttu-id="9b3ff-111">Pode definir manipuladores de eventos de interface do usuário, associar a dados de entrada e gerenciar seu próprio ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
* <span data-ttu-id="9b3ff-112">Normalmente é definido em um arquivo *. Razor* usando sintaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="9b3ff-113">Uma introdução ao Razor</span><span class="sxs-lookup"><span data-stu-id="9b3ff-113">An introduction to Razor</span></span>

<span data-ttu-id="9b3ff-114">O Razor é uma linguagem de modelagem de marcação leve com base em C#HTML e.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="9b3ff-115">Com o Razor, você pode fazer a transição diretamente entre C# a marcação e o código para definir a lógica de renderização do componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="9b3ff-116">Quando o arquivo *. Razor* é compilado, a lógica de renderização é capturada de forma estruturada em uma classe do .net.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="9b3ff-117">O nome da classe compilada é extraído do nome do arquivo *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="9b3ff-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="9b3ff-118">O namespace é extraído do namespace padrão para o projeto e o caminho da pasta, ou você pode especificar explicitamente o namespace usando a diretiva `@namespace` (mais sobre as diretivas do Razor abaixo).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="9b3ff-119">A lógica de renderização de um componente é criada usando marcação HTML normal com lógica dinâmica adicionada C#usando.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="9b3ff-120">O caractere `@` é usado para fazer a C#transição para.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="9b3ff-121">O Razor normalmente é inteligente para descobrir quando você volta para o HTML.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="9b3ff-122">Por exemplo, o componente a seguir renderiza uma marca `<p>` com a hora atual:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="9b3ff-123">Para especificar explicitamente o início e o final de C# uma expressão, use parênteses:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="9b3ff-124">O Razor também facilita o uso C# do fluxo de controle na lógica de renderização.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="9b3ff-125">Por exemplo, você pode renderizar condicionalmente um HTML como este:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="9b3ff-126">Ou você pode gerar uma lista de itens usando um loop C# `foreach` normal como este:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

<span data-ttu-id="9b3ff-127">As diretivas do Razor, como diretivas no ASP.NET Web Forms, controlam muitos aspectos de como um componente Razor é compilado.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="9b3ff-128">Os exemplos incluem o componente:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-128">Examples include the component's:</span></span>

* <span data-ttu-id="9b3ff-129">Namespace</span><span class="sxs-lookup"><span data-stu-id="9b3ff-129">Namespace</span></span>
* <span data-ttu-id="9b3ff-130">Classe base</span><span class="sxs-lookup"><span data-stu-id="9b3ff-130">Base class</span></span>
* <span data-ttu-id="9b3ff-131">Interfaces implementadas</span><span class="sxs-lookup"><span data-stu-id="9b3ff-131">Implemented interfaces</span></span>
* <span data-ttu-id="9b3ff-132">Parâmetros genéricos</span><span class="sxs-lookup"><span data-stu-id="9b3ff-132">Generic parameters</span></span>
* <span data-ttu-id="9b3ff-133">Namespaces importados</span><span class="sxs-lookup"><span data-stu-id="9b3ff-133">Imported namespaces</span></span>
* <span data-ttu-id="9b3ff-134">Rotas</span><span class="sxs-lookup"><span data-stu-id="9b3ff-134">Routes</span></span>

<span data-ttu-id="9b3ff-135">As diretivas do Razor começam com o caractere `@` e são normalmente usadas no início de uma nova linha no início do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="9b3ff-136">Por exemplo, a diretiva `@namespace` define o namespace do componente:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="9b3ff-137">A tabela a seguir resume as várias diretivas Razor usadas no mais e suas ASP.NET Web Forms equivalentes, se existirem.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="9b3ff-138">Diretiva</span><span class="sxs-lookup"><span data-stu-id="9b3ff-138">Directive</span></span>    |<span data-ttu-id="9b3ff-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b3ff-139">Description</span></span>|<span data-ttu-id="9b3ff-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b3ff-140">Example</span></span>|<span data-ttu-id="9b3ff-141">Web Forms equivalente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="9b3ff-142">Adiciona um atributo de nível de classe ao componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="9b3ff-143">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9b3ff-143">None</span></span>|
|`@code`      |<span data-ttu-id="9b3ff-144">Adiciona membros de classe ao componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="9b3ff-145">Implementa a interface especificada</span><span class="sxs-lookup"><span data-stu-id="9b3ff-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="9b3ff-146">Usar code-behind</span><span class="sxs-lookup"><span data-stu-id="9b3ff-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="9b3ff-147">Herda da classe base especificada</span><span class="sxs-lookup"><span data-stu-id="9b3ff-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="9b3ff-148">Injeta um serviço no componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="9b3ff-149">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9b3ff-149">None</span></span>|
|`@layout`    |<span data-ttu-id="9b3ff-150">Especifica um componente de layout para o componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="9b3ff-151">Define o namespace para o componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="9b3ff-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9b3ff-152">None</span></span>|
|`@page`      |<span data-ttu-id="9b3ff-153">Especifica a rota para o componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="9b3ff-154">Especifica um parâmetro de tipo genérico para o componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="9b3ff-155">Usar code-behind</span><span class="sxs-lookup"><span data-stu-id="9b3ff-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="9b3ff-156">Especifica um namespace para trazer para o escopo</span><span class="sxs-lookup"><span data-stu-id="9b3ff-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="9b3ff-157">Adicionar namespace em *Web. config*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="9b3ff-158">Os componentes do Razor também fazem uso extensivo de *atributos de diretiva* em elementos para controlar vários aspectos de como os componentes são compilados (manipulação de eventos, vinculação de dados, referências de elementos de & de componentes e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="9b3ff-159">Atributos de diretiva seguem uma sintaxe genérica comum em que os valores entre parênteses são opcionais:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="9b3ff-160">A tabela a seguir resume os vários atributos para as diretivas do Razor usadas no mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="9b3ff-161">Atributo</span><span class="sxs-lookup"><span data-stu-id="9b3ff-161">Attribute</span></span>    |<span data-ttu-id="9b3ff-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b3ff-162">Description</span></span>|<span data-ttu-id="9b3ff-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b3ff-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="9b3ff-164">Renderiza um dicionário de atributos</span><span class="sxs-lookup"><span data-stu-id="9b3ff-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="9b3ff-165">Cria uma associação de dados bidirecional</span><span class="sxs-lookup"><span data-stu-id="9b3ff-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="9b3ff-166">Adiciona um manipulador de eventos para o evento especificado</span><span class="sxs-lookup"><span data-stu-id="9b3ff-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="9b3ff-167">Especifica uma chave a ser usada pelo algoritmo diff para preservar elementos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="9b3ff-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="9b3ff-168">Captura uma referência para o componente ou elemento HTML</span><span class="sxs-lookup"><span data-stu-id="9b3ff-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="9b3ff-169">Os vários atributos de diretiva usados pelo mais recente (`@onclick`, `@bind`, `@ref` e assim por diante) são abordados nas seções abaixo e nos capítulos posteriores.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="9b3ff-170">Muitas das sintaxes usadas em arquivos *. aspx* e *. ascx* têm sintaxes paralelas no Razor.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="9b3ff-171">Veja abaixo uma comparação simples das sintaxes para ASP.NET Web Forms e Razor.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="9b3ff-172">Recurso</span><span class="sxs-lookup"><span data-stu-id="9b3ff-172">Feature</span></span>                      |<span data-ttu-id="9b3ff-173">Web Forms</span><span class="sxs-lookup"><span data-stu-id="9b3ff-173">Web Forms</span></span>           |<span data-ttu-id="9b3ff-174">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b3ff-174">Syntax</span></span>               |<span data-ttu-id="9b3ff-175">Razor</span><span class="sxs-lookup"><span data-stu-id="9b3ff-175">Razor</span></span>         |<span data-ttu-id="9b3ff-176">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b3ff-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="9b3ff-177">Diretivas</span><span class="sxs-lookup"><span data-stu-id="9b3ff-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="9b3ff-178">Blocos de código</span><span class="sxs-lookup"><span data-stu-id="9b3ff-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="9b3ff-179">Expressões</span><span class="sxs-lookup"><span data-stu-id="9b3ff-179">Expressions</span></span><br><span data-ttu-id="9b3ff-180">(Codificado em HTML)</span><span class="sxs-lookup"><span data-stu-id="9b3ff-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="9b3ff-181">Implícito: `@`</span><span class="sxs-lookup"><span data-stu-id="9b3ff-181">Implicit: `@`</span></span><br><span data-ttu-id="9b3ff-182">Explicit: `@()`</span><span class="sxs-lookup"><span data-stu-id="9b3ff-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="9b3ff-183">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b3ff-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="9b3ff-184">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="9b3ff-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="9b3ff-185">Para adicionar membros à classe de componente Razor, use a diretiva `@code`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="9b3ff-186">Essa técnica é semelhante ao uso de um bloco `<script runat="server">...</script>` em um ASP.NET Web Forms controle de usuário ou página.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="9b3ff-187">Como o Razor se baseia C#em, ele deve ser compilado de dentro C# de um projeto ( *. csproj*).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="9b3ff-188">Não é possível compilar arquivos *. Razor* de um projeto VB ( *. vbproj*).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-188">You can't compile *.razor* files from a VB project (*.vbproj*).</span></span> <span data-ttu-id="9b3ff-189">Você ainda pode fazer referência a projetos do VB por meio de seu projeto mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-189">You can still reference VB projects from your Blazor project.</span></span> <span data-ttu-id="9b3ff-190">O oposto também é verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-190">The opposite is true too.</span></span>

<span data-ttu-id="9b3ff-191">Para obter uma referência completa de sintaxe Razor, consulte [referência de sintaxe Razor para ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="9b3ff-192">Usar componentes</span><span class="sxs-lookup"><span data-stu-id="9b3ff-192">Use components</span></span>

<span data-ttu-id="9b3ff-193">Além do HTML normal, os componentes também podem usar outros componentes como parte da lógica de renderização.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="9b3ff-194">A sintaxe para usar um componente no Razor é semelhante ao uso de um controle de usuário em um aplicativo ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="9b3ff-195">Os componentes são especificados usando uma marca de elemento que corresponde ao nome do tipo do componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="9b3ff-196">Por exemplo, você pode adicionar um componente `Counter` como este:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="9b3ff-197">Ao contrário de ASP.NET Web Forms, os componentes do mais incrivelmente:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

* <span data-ttu-id="9b3ff-198">Não use um prefixo de elemento (por exemplo, `asp:`).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-198">Don't use an element prefix (for example, `asp:`).</span></span>
* <span data-ttu-id="9b3ff-199">Não exija o registro na página ou no *Web. config*.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="9b3ff-200">Imagine os componentes do Razor como você faria com os tipos do .NET, pois isso é exatamente o que eles são.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="9b3ff-201">Se o assembly que contém o componente for referenciado, o componente estará disponível para uso.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="9b3ff-202">Para colocar o namespace do componente no escopo, aplique a diretiva `@using`:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="9b3ff-203">Como visto nos projetos de mais alto padrão, é comum colocar diretivas `@using` em um arquivo *_Imports. Razor* para que elas sejam importadas para todos os arquivos *. Razor* no mesmo diretório e em diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="9b3ff-204">Se o namespace de um componente não estiver no escopo, você poderá especificar um componente usando seu nome de tipo completo, como você C#pode:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="9b3ff-205">Parâmetros do componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-205">Component parameters</span></span>

<span data-ttu-id="9b3ff-206">No ASP.NET Web Forms, você pode fluir parâmetros e dados para controles usando propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="9b3ff-207">Essas propriedades podem ser definidas na marcação usando atributos ou definidos diretamente no código.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="9b3ff-208">Os componentes mais úteis funcionam de maneira semelhante, embora as propriedades do componente também devam ser marcadas com o atributo `[Parameter]` para serem considerados parâmetros de componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="9b3ff-209">O componente `Counter` a seguir define um parâmetro de componente chamado `IncrementAmount` que pode ser usado para especificar o valor que o `Counter` deve ser incrementado cada vez que o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="9b3ff-210">Para especificar um parâmetro de componente no mais bem, use um atributo como você faria em ASP.NET Web Forms:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="9b3ff-211">Manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="9b3ff-211">Event handlers</span></span>

<span data-ttu-id="9b3ff-212">O ASP.NET Web Forms e o mais bem fornecem um modelo de programação baseado em eventos para manipular eventos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="9b3ff-213">Exemplos desses eventos incluem cliques de botão e entrada de texto.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="9b3ff-214">No ASP.NET Web Forms, você usa controles de servidor HTML para manipular eventos de interface do usuário expostos pelo DOM ou pode manipular eventos expostos por controles de servidor Web.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="9b3ff-215">Os eventos são exibidos no servidor por meio de solicitações de postback de formulário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="9b3ff-216">Considere o seguinte Web Forms exemplo de clique de botão:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="9b3ff-217">*Counter. ascx*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="9b3ff-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="9b3ff-219">No mais claro, você pode registrar manipuladores para eventos da interface do usuário DOM diretamente usando atributos de diretiva do formulário `@on{event}`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="9b3ff-220">O espaço reservado `{event}` representa o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="9b3ff-221">Por exemplo, você pode ouvir cliques de botão como este:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="9b3ff-222">Os manipuladores de eventos podem aceitar um argumento opcional, específico do evento, para fornecer mais informações sobre o evento.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="9b3ff-223">Por exemplo, eventos de mouse podem usar um argumento `MouseEventArgs`, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e) 
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="9b3ff-224">Em vez de fazer referência a um grupo de métodos para um manipulador de eventos, você pode usar uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="9b3ff-225">Uma expressão lambda permite que você feche outros valores no escopo.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="9b3ff-226">Os manipuladores de eventos podem ser executados de forma síncrona ou assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="9b3ff-227">Por exemplo, o seguinte manipulador de eventos `OnClick` é executado de forma assíncrona:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick() 
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="9b3ff-228">Depois que um evento é manipulado, o componente é renderizado para considerar qualquer alteração de estado de componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="9b3ff-229">Com manipuladores de eventos assíncronos, o componente é renderizado imediatamente após a execução do manipulador ser concluída.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="9b3ff-230">O componente é renderizado *novamente* após a conclusão do `Task` assíncrono.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="9b3ff-231">Esse modo de execução assíncrono fornece uma oportunidade de renderizar alguma interface do usuário apropriada enquanto o `Task` assíncrono ainda está em andamento.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="Get message">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code 
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="9b3ff-232">Os componentes também podem definir seus próprios eventos definindo um parâmetro de componente do tipo `EventCallback<TValue>`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="9b3ff-233">Os retornos de chamada de evento dão suporte a todas as variações de manipuladores de eventos de interface do usuário DOM: argumentos opcionais, síncronos ou assíncronos, grupos de métodos ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="9b3ff-234">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="9b3ff-234">Data binding</span></span>

<span data-ttu-id="9b3ff-235">O mais fácil é um mecanismo simples para associar dados de um componente de interface do usuário ao estado do componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="9b3ff-236">Essa abordagem difere dos recursos do ASP.NET Web Forms para associação de dados de fontes de dados a controles de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="9b3ff-237">Abordaremos o tratamento de dados de fontes de dados diferentes na seção [lidando com dados](data.md) .</span><span class="sxs-lookup"><span data-stu-id="9b3ff-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="9b3ff-238">Para criar uma associação de dados bidirecional de um componente de interface do usuário para o estado do componente, use o atributo de diretiva `@bind`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="9b3ff-239">No exemplo a seguir, o valor da caixa de seleção está associado ao campo `isChecked`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="9b3ff-240">Quando o componente é renderizado, o valor da caixa de seleção é definido como o valor do campo `isChecked`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="9b3ff-241">Quando o usuário alterna a caixa de seleção, o evento `onchange` é acionado e o campo `isChecked` é definido como o novo valor.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="9b3ff-242">Nesse caso, a sintaxe `@bind` é equivalente à seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="9b3ff-243">Para alterar o evento usado para a associação, use o atributo `@bind:event`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="9b3ff-244">Os componentes também podem dar suporte à ligação de dados com seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="9b3ff-245">Para associação de dados, defina um parâmetro de retorno de chamada de evento com o mesmo nome que o parâmetro acoplável.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="9b3ff-246">O sufixo "alterado" é adicionado ao nome.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="9b3ff-247">*PasswordBox. Razor*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-247">*PasswordBox.razor*</span></span>

```razor
Password: <input 
    value="@Password" 
    @oninput="OnPasswordChanged" 
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="9b3ff-248">Para encadear uma associação de dados a um elemento subjacente da interface do usuário, defina o valor e manipule o evento diretamente no elemento da interface do usuário em vez de usar o atributo `@bind`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="9b3ff-249">Para associar a um parâmetro de componente, use um atributo `@bind-{Parameter}` para especificar o parâmetro ao qual você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="9b3ff-250">Alterações de estado</span><span class="sxs-lookup"><span data-stu-id="9b3ff-250">State changes</span></span>

<span data-ttu-id="9b3ff-251">Se o estado do componente foi alterado fora de um evento de interface do usuário normal ou de retorno de chamada de evento, o componente deve sinalizar manualmente que ele precisa ser processado novamente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="9b3ff-252">Para sinalizar que o estado de um componente foi alterado, chame o método `StateHasChanged` no componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="9b3ff-253">No exemplo a seguir, um componente exibe uma mensagem de um serviço `AppState` que pode ser atualizado por outras partes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="9b3ff-254">O componente registra seu método `StateHasChanged` com o evento `AppState.OnChange` para que o componente seja renderizado sempre que a mensagem é atualizada.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="9b3ff-255">Ciclo de vida do componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-255">Component lifecycle</span></span>

<span data-ttu-id="9b3ff-256">O ASP.NET Web Forms Framework tem métodos de ciclo de vida bem definidos para módulos, páginas e controles.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="9b3ff-257">Por exemplo, o controle a seguir implementa manipuladores de eventos para os eventos de ciclo de vida `Init`, `Load` e `UnLoad`:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="9b3ff-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="9b3ff-259">Os componentes mais fáceis também têm um ciclo de vida bem definido.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="9b3ff-260">O ciclo de vida de um componente pode ser usado para inicializar o estado do componente e implementar comportamentos avançados de componentes.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span> 

<span data-ttu-id="9b3ff-261">Todos os métodos de ciclo de vida de componentes de mais de um dos outros são síncronos e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="9b3ff-262">A renderização do componente é síncrona.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-262">Component rendering is synchronous.</span></span> <span data-ttu-id="9b3ff-263">Não é possível executar a lógica assíncrona como parte da renderização do componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="9b3ff-264">Toda a lógica assíncrona deve ser executada como parte de um método de ciclo de vida `async`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="9b3ff-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="9b3ff-265">OnInitialized</span></span>

<span data-ttu-id="9b3ff-266">Os métodos `OnInitialized` e `OnInitializedAsync` são usados para inicializar o componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="9b3ff-267">Um componente é normalmente inicializado após sua primeira renderização.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="9b3ff-268">Depois que um componente é inicializado, ele pode ser renderizado várias vezes antes de ser Descartado.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="9b3ff-269">O método `OnInitialized` é semelhante ao evento `Page_Load` no ASP.NET Web Forms páginas e controles.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="9b3ff-270">Parameterset</span><span class="sxs-lookup"><span data-stu-id="9b3ff-270">OnParametersSet</span></span>

<span data-ttu-id="9b3ff-271">Os métodos `OnParametersSet` e `OnParametersSetAsync` são chamados quando um componente recebe parâmetros de seu pai e o valor é atribuído a propriedades.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="9b3ff-272">Esses métodos são executados após a inicialização do componente e *cada vez que o componente é renderizado*.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="9b3ff-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="9b3ff-273">OnAfterRender</span></span>

<span data-ttu-id="9b3ff-274">Os métodos `OnAfterRender` e `OnAfterRenderAsync` são chamados após a conclusão da renderização de um componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="9b3ff-275">Referências de elemento e componente são preenchidas neste ponto (mais sobre esses conceitos abaixo).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="9b3ff-276">A interatividade com o navegador está habilitada neste ponto.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="9b3ff-277">As interações com a execução do DOM e do JavaScript podem ocorrer com segurança.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span> 

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="9b3ff-278">`OnAfterRender` e `OnAfterRenderAsync` *não são chamados durante o pré-processamento no servidor*.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="9b3ff-279">O parâmetro `firstRender` é `true` na primeira vez que o componente é renderizado; caso contrário, seu valor será `false`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="9b3ff-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="9b3ff-280">IDisposable</span></span>

<span data-ttu-id="9b3ff-281">Os componentes mais fáceis podem implementar `IDisposable` para descartar os recursos quando o componente é removido da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="9b3ff-282">Um componente Razor pode implementar `IDispose` usando a diretiva `@implements`:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="9b3ff-283">Capturar referências de componente</span><span class="sxs-lookup"><span data-stu-id="9b3ff-283">Capture component references</span></span>

<span data-ttu-id="9b3ff-284">No ASP.NET Web Forms, é comum manipular uma instância de controle diretamente no código, referindo-se à sua ID.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="9b3ff-285">No mais grande, também é possível capturar e manipular uma referência a um componente, embora seja muito menos comum.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="9b3ff-286">Para capturar uma referência de componente no mais alto, use o atributo de diretiva `@ref`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="9b3ff-287">O valor do atributo deve corresponder ao nome de um campo configurável com o mesmo tipo do componente referenciado.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="9b3ff-288">Quando o componente pai é renderizado, o campo é populado com a instância de componente filho.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="9b3ff-289">Em seguida, você pode chamar métodos em, ou então manipular, a instância do componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="9b3ff-290">Não é recomendável manipular o estado do componente diretamente usando referências de componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="9b3ff-291">Isso impede que o componente seja renderizado automaticamente nos horários corretos.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="9b3ff-292">Capturar referências de elemento</span><span class="sxs-lookup"><span data-stu-id="9b3ff-292">Capture element references</span></span>

<span data-ttu-id="9b3ff-293">Os componentes mais poseriais podem capturar referências a um elemento.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="9b3ff-294">Ao contrário dos controles de servidor HTML no ASP.NET Web Forms, você não pode manipular o DOM diretamente usando uma referência de elemento no mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="9b3ff-295">O mais incrivelmente lida com a maioria das interações de DOM para você usando seu algoritmo de comparação DOM.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="9b3ff-296">Referências de elemento capturado no mais incrivelmente são opacas.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="9b3ff-297">No entanto, eles são usados para passar uma referência de elemento específica em uma chamada de interoperabilidade JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="9b3ff-298">Para obter mais informações sobre a interoperabilidade de JavaScript, consulte [ASP.NET Core a interoperabilidade de JavaScript mais incrivelmente](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="9b3ff-299">Componentes de modelo</span><span class="sxs-lookup"><span data-stu-id="9b3ff-299">Templated components</span></span>

<span data-ttu-id="9b3ff-300">No ASP.NET Web Forms, você pode criar *controles modelo*.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="9b3ff-301">Controles de modelo permitem que o desenvolvedor especifique uma parte do HTML usada para renderizar um controle de contêiner.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="9b3ff-302">A mecânica da criação de controles de servidor modelo é complexa, mas permite cenários poderosos para a renderização de dados em uma maneira personalizável do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="9b3ff-303">Exemplos de controles de modelo incluem `Repeater` e `DataList`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-303">Examples of templated controls include `Repeater` and `DataList`.</span></span> 

<span data-ttu-id="9b3ff-304">Os componentes mais fáceis também podem ser modelados definindo parâmetros de componente do tipo `RenderFragment` ou `RenderFragment<T>`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="9b3ff-305">Um `RenderFragment` representa uma parte da marcação Razor que pode ser renderizada pelo componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="9b3ff-306">Um `RenderFragment<T>` é uma parte da marcação Razor que usa um parâmetro que pode ser especificado quando o fragmento de renderização é renderizado.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="9b3ff-307">Conteúdo filho</span><span class="sxs-lookup"><span data-stu-id="9b3ff-307">Child content</span></span>

<span data-ttu-id="9b3ff-308">Os componentes mais fáceis podem capturar seu conteúdo filho como um `RenderFragment` e renderizar esse conteúdo como parte da renderização do componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="9b3ff-309">Para capturar o conteúdo filho, defina um parâmetro de componente do tipo `RenderFragment` e nomeie-o `ChildContent`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="9b3ff-310">*ChildContentComponent. Razor*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="9b3ff-311">Um componente pai pode fornecer conteúdo filho usando sintaxe Razor normal.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="9b3ff-312">Parâmetros do modelo</span><span class="sxs-lookup"><span data-stu-id="9b3ff-312">Template parameters</span></span>

<span data-ttu-id="9b3ff-313">Um componente de mais alto modelo também pode definir vários parâmetros de componente do tipo `RenderFragment` ou `RenderFragment<T>`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="9b3ff-314">O parâmetro para um `RenderFragment<T>` pode ser especificado quando é invocado.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="9b3ff-315">Para especificar um parâmetro de tipo genérico para um componente, use a diretiva `@typeparam` Razor.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="9b3ff-316">*SimpleListView. Razor*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="9b3ff-317">Ao usar um componente modelo, os parâmetros do modelo podem ser especificados usando elementos filho que correspondem aos nomes dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="9b3ff-318">Os argumentos de componente do tipo `RenderFragment<T>` passados como elementos têm um parâmetro implícito denominado `context`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="9b3ff-319">Você pode alterar o nome desse parâmetro de implementação usando o atributo `Context` no elemento filho.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="9b3ff-320">Qualquer parâmetro de tipo genérico pode ser especificado usando um atributo que corresponde ao nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="9b3ff-321">O parâmetro de tipo será inferido se possível:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="9b3ff-322">A saída desse componente tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="9b3ff-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="9b3ff-323">Code-behind</span><span class="sxs-lookup"><span data-stu-id="9b3ff-323">Code-behind</span></span>

<span data-ttu-id="9b3ff-324">Um componente mais simples normalmente é criado em um único arquivo *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="9b3ff-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="9b3ff-325">No entanto, também é possível separar o código e a marcação usando um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="9b3ff-326">Para usar um arquivo de componente, adicione C# um arquivo que corresponda ao nome do arquivo do componente, mas com uma extensão *. cs* adicionada (*Counter.Razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="9b3ff-327">Use o C# arquivo para definir uma classe base para o componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="9b3ff-328">Você pode nomear a classe base como quiser, mas é comum nomear a classe da mesma forma que a classe de componente, mas com uma extensão `Base` adicionada (`CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="9b3ff-329">A classe baseada em componente também deve derivar de `ComponentBase`.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="9b3ff-330">Em seguida, no arquivo de componente Razor, adicione a diretiva `@inherits` para especificar a classe base para o componente (`@inherits CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="9b3ff-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="9b3ff-331">*Counter. Razor*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="9b3ff-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="9b3ff-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase 
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="9b3ff-333">A visibilidade dos membros do componente na classe base deve ser `protected` ou `public` para ser visível para a classe de componente.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9b3ff-334">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="9b3ff-334">Additional resources</span></span>

<span data-ttu-id="9b3ff-335">O anterior não é um tratamento completo de todos os aspectos dos componentes mais completos.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="9b3ff-336">Para obter mais informações sobre como [criar e usar ASP.NET Core componentes do Razor](/aspnet/core/blazor/components), consulte a documentação mais bem.</span><span class="sxs-lookup"><span data-stu-id="9b3ff-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9b3ff-337">[Anterior](app-startup.md)
>[Próximo](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="9b3ff-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
