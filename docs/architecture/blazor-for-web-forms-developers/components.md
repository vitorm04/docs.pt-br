---
title: Construa componentes de IU reutilizáveis com Blazor
description: Aprenda a construir componentes de IU reutilizáveis com o Blazor e como eles se comparam aos controles ASP.NET Web Forms.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228623"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="47d02-103">Construa componentes de IU reutilizáveis com Blazor</span><span class="sxs-lookup"><span data-stu-id="47d02-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="47d02-104">Uma das coisas bonitas sobre ASP.NET Web Forms é como ele permite o encapsulamento de peças reutilizáveis do código de interface do usuário (UI) em controles de interface do usuário reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="47d02-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="47d02-105">Controles personalizados do usuário podem ser definidos em marcação usando arquivos *.ascx.*</span><span class="sxs-lookup"><span data-stu-id="47d02-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="47d02-106">Você também pode construir controles de servidor elaborados em código com suporte completo ao designer.</span><span class="sxs-lookup"><span data-stu-id="47d02-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="47d02-107">Blazor também suporta encapsulamento de IU através de *componentes*.</span><span class="sxs-lookup"><span data-stu-id="47d02-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="47d02-108">Um componente:</span><span class="sxs-lookup"><span data-stu-id="47d02-108">A component:</span></span>

- <span data-ttu-id="47d02-109">É um pedaço independente de ui.</span><span class="sxs-lookup"><span data-stu-id="47d02-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="47d02-110">Mantém seu próprio estado e lógica de renderização.</span><span class="sxs-lookup"><span data-stu-id="47d02-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="47d02-111">Pode definir manipuladores de eventos de ui, vincular-se a dados de entrada e gerenciar seu próprio ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="47d02-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="47d02-112">É tipicamente definido em um arquivo *.razor* usando sintaxe de navalha.</span><span class="sxs-lookup"><span data-stu-id="47d02-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="47d02-113">Uma introdução a Razor</span><span class="sxs-lookup"><span data-stu-id="47d02-113">An introduction to Razor</span></span>

<span data-ttu-id="47d02-114">Razor é uma linguagem de marcação leve baseada em HTML e C#.</span><span class="sxs-lookup"><span data-stu-id="47d02-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="47d02-115">Com razor, você pode fazer uma transição perfeita entre o código de marcação e c# para definir sua lógica de renderização de componentes.</span><span class="sxs-lookup"><span data-stu-id="47d02-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="47d02-116">Quando o arquivo *.razor* é compilado, a lógica de renderização é capturada de forma estruturada em uma classe .NET.</span><span class="sxs-lookup"><span data-stu-id="47d02-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="47d02-117">O nome da classe compilada é retirado do nome do arquivo *.razor.*</span><span class="sxs-lookup"><span data-stu-id="47d02-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="47d02-118">O namespace é retirado do namespace padrão para o projeto e o caminho da `@namespace` pasta, ou você pode especificar explicitamente o namespace usando a diretiva (mais em diretivas de Navalha abaixo).</span><span class="sxs-lookup"><span data-stu-id="47d02-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="47d02-119">A lógica de renderização de um componente é de autoria usando marcação HTML normal com lógica dinâmica adicionada usando C#.</span><span class="sxs-lookup"><span data-stu-id="47d02-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="47d02-120">O `@` personagem é usado para fazer a transição para C#.</span><span class="sxs-lookup"><span data-stu-id="47d02-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="47d02-121">Razor é tipicamente inteligente em descobrir quando você mudou de volta para HTML.</span><span class="sxs-lookup"><span data-stu-id="47d02-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="47d02-122">Por exemplo, o seguinte `<p>` componente renderiza uma tag com o tempo atual:</span><span class="sxs-lookup"><span data-stu-id="47d02-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="47d02-123">Para especificar explicitamente o início e o fim de uma expressão C#, use parênteses:</span><span class="sxs-lookup"><span data-stu-id="47d02-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="47d02-124">Razor também facilita o uso do fluxo de controle C# em sua lógica de renderização.</span><span class="sxs-lookup"><span data-stu-id="47d02-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="47d02-125">Por exemplo, você pode condicionalmente renderizar alguns HTML como este:</span><span class="sxs-lookup"><span data-stu-id="47d02-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="47d02-126">Ou você pode gerar uma lista de itens `foreach` usando um loop C# normal como este:</span><span class="sxs-lookup"><span data-stu-id="47d02-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="47d02-127">As diretivas de navalha, como as diretivas em ASP.NET Formulários da Web, controlam muitos aspectos de como um componente Razor é compilado.</span><span class="sxs-lookup"><span data-stu-id="47d02-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="47d02-128">Exemplos incluem os componentes:</span><span class="sxs-lookup"><span data-stu-id="47d02-128">Examples include the component's:</span></span>

- <span data-ttu-id="47d02-129">Namespace</span><span class="sxs-lookup"><span data-stu-id="47d02-129">Namespace</span></span>
- <span data-ttu-id="47d02-130">Classe base</span><span class="sxs-lookup"><span data-stu-id="47d02-130">Base class</span></span>
- <span data-ttu-id="47d02-131">Interfaces implementadas</span><span class="sxs-lookup"><span data-stu-id="47d02-131">Implemented interfaces</span></span>
- <span data-ttu-id="47d02-132">Parâmetros genéricos</span><span class="sxs-lookup"><span data-stu-id="47d02-132">Generic parameters</span></span>
- <span data-ttu-id="47d02-133">Namespaces importados</span><span class="sxs-lookup"><span data-stu-id="47d02-133">Imported namespaces</span></span>
- <span data-ttu-id="47d02-134">Rotas</span><span class="sxs-lookup"><span data-stu-id="47d02-134">Routes</span></span>

<span data-ttu-id="47d02-135">As diretivas de `@` navalha começam com o caractere e são normalmente usadas no início de uma nova linha no início do arquivo.</span><span class="sxs-lookup"><span data-stu-id="47d02-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="47d02-136">Por exemplo, `@namespace` a diretiva define o espaço de nome do componente:</span><span class="sxs-lookup"><span data-stu-id="47d02-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="47d02-137">A tabela a seguir resume as várias diretivas de Navalha usadas em Blazor e seus ASP.NET equivalentes web forms, se existirem.</span><span class="sxs-lookup"><span data-stu-id="47d02-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="47d02-138">Diretiva</span><span class="sxs-lookup"><span data-stu-id="47d02-138">Directive</span></span>    |<span data-ttu-id="47d02-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="47d02-139">Description</span></span>|<span data-ttu-id="47d02-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47d02-140">Example</span></span>|<span data-ttu-id="47d02-141">Formulários web equivalentes</span><span class="sxs-lookup"><span data-stu-id="47d02-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="47d02-142">Adiciona um atributo de nível de classe ao componente</span><span class="sxs-lookup"><span data-stu-id="47d02-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="47d02-143">Nenhum</span><span class="sxs-lookup"><span data-stu-id="47d02-143">None</span></span>|
|`@code`      |<span data-ttu-id="47d02-144">Adiciona membros da classe ao componente</span><span class="sxs-lookup"><span data-stu-id="47d02-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="47d02-145">Implementa a interface especificada</span><span class="sxs-lookup"><span data-stu-id="47d02-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="47d02-146">Usar code-behind</span><span class="sxs-lookup"><span data-stu-id="47d02-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="47d02-147">Herda da classe base especificada</span><span class="sxs-lookup"><span data-stu-id="47d02-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="47d02-148">Injeta um serviço no componente</span><span class="sxs-lookup"><span data-stu-id="47d02-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="47d02-149">Nenhum</span><span class="sxs-lookup"><span data-stu-id="47d02-149">None</span></span>|
|`@layout`    |<span data-ttu-id="47d02-150">Especifica um componente de layout para o componente</span><span class="sxs-lookup"><span data-stu-id="47d02-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="47d02-151">Define o namespace para o componente</span><span class="sxs-lookup"><span data-stu-id="47d02-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="47d02-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="47d02-152">None</span></span>|
|`@page`      |<span data-ttu-id="47d02-153">Especifica a rota para o componente</span><span class="sxs-lookup"><span data-stu-id="47d02-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="47d02-154">Especifica um parâmetro de tipo genérico para o componente</span><span class="sxs-lookup"><span data-stu-id="47d02-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="47d02-155">Usar code-behind</span><span class="sxs-lookup"><span data-stu-id="47d02-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="47d02-156">Especifica um namespace para trazer para o escopo</span><span class="sxs-lookup"><span data-stu-id="47d02-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="47d02-157">Adicionar namespace em *web.config*</span><span class="sxs-lookup"><span data-stu-id="47d02-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="47d02-158">Os componentes da navalha também fazem uso extensivo de *atributos de diretiva sobre elementos* para controlar vários aspectos de como os componentes são compilados (manipulação de eventos, vinculação de dados, referências de elementos & componentes, e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="47d02-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="47d02-159">Todos os atributos diretivos seguem uma sintaxe genérica comum onde os valores entre parênteses são opcionais:</span><span class="sxs-lookup"><span data-stu-id="47d02-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="47d02-160">A tabela a seguir resume os vários atributos para as diretivas de Razor usadas em Blazor.</span><span class="sxs-lookup"><span data-stu-id="47d02-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="47d02-161">Atributo</span><span class="sxs-lookup"><span data-stu-id="47d02-161">Attribute</span></span>    |<span data-ttu-id="47d02-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="47d02-162">Description</span></span>|<span data-ttu-id="47d02-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47d02-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="47d02-164">Torna um dicionário de atributos</span><span class="sxs-lookup"><span data-stu-id="47d02-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="47d02-165">Cria uma vinculação de dados bidirecional</span><span class="sxs-lookup"><span data-stu-id="47d02-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="47d02-166">Adiciona um manipulador de eventos para o evento especificado</span><span class="sxs-lookup"><span data-stu-id="47d02-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="47d02-167">Especifica uma chave a ser usada pelo algoritmo de difusão para preservar elementos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="47d02-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="47d02-168">Captura uma referência ao componente ou elemento HTML</span><span class="sxs-lookup"><span data-stu-id="47d02-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="47d02-169">Os vários atributos diretivos `@bind` `@ref`utilizados por Blazor (`@onclick`, , e assim por diante) são cobertos nas seções abaixo e capítulos posteriores.</span><span class="sxs-lookup"><span data-stu-id="47d02-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="47d02-170">Muitas das sintaxe usadas em arquivos *.aspx* e *.ascx* têm sintaxes paralelas em Razor.</span><span class="sxs-lookup"><span data-stu-id="47d02-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="47d02-171">Abaixo está uma simples comparação das sintaxes para ASP.NET Formulários web e navalha.</span><span class="sxs-lookup"><span data-stu-id="47d02-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="47d02-172">Recurso</span><span class="sxs-lookup"><span data-stu-id="47d02-172">Feature</span></span>                      |<span data-ttu-id="47d02-173">Formulários da Web</span><span class="sxs-lookup"><span data-stu-id="47d02-173">Web Forms</span></span>           |<span data-ttu-id="47d02-174">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47d02-174">Syntax</span></span>               |<span data-ttu-id="47d02-175">Razor</span><span class="sxs-lookup"><span data-stu-id="47d02-175">Razor</span></span>         |<span data-ttu-id="47d02-176">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47d02-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="47d02-177">Diretivas</span><span class="sxs-lookup"><span data-stu-id="47d02-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="47d02-178">Blocos de códigos</span><span class="sxs-lookup"><span data-stu-id="47d02-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="47d02-179">Expressões</span><span class="sxs-lookup"><span data-stu-id="47d02-179">Expressions</span></span><br><span data-ttu-id="47d02-180">(CODIFICAdo em HTML)</span><span class="sxs-lookup"><span data-stu-id="47d02-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="47d02-181">Implícita:`@`</span><span class="sxs-lookup"><span data-stu-id="47d02-181">Implicit: `@`</span></span><br><span data-ttu-id="47d02-182">Explícita:`@()`</span><span class="sxs-lookup"><span data-stu-id="47d02-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="47d02-183">Comentários</span><span class="sxs-lookup"><span data-stu-id="47d02-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="47d02-184">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="47d02-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="47d02-185">Para adicionar membros à classe de `@code` componentes Razor, use a diretiva.</span><span class="sxs-lookup"><span data-stu-id="47d02-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="47d02-186">Essa técnica é semelhante `<script runat="server">...</script>` ao uso de um bloco em um ASP.NET o controle ou página do usuário do Web Forms.</span><span class="sxs-lookup"><span data-stu-id="47d02-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="47d02-187">Como razor é baseado em C#, ele deve ser compilado a partir de um projeto C# (*.csproj*).</span><span class="sxs-lookup"><span data-stu-id="47d02-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="47d02-188">Você não pode compilar *arquivos .razor* de um projeto Visual Basic (*.vbproj*).</span><span class="sxs-lookup"><span data-stu-id="47d02-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="47d02-189">Você ainda pode referenciar projetos Visual Basic do seu projeto Blazor.</span><span class="sxs-lookup"><span data-stu-id="47d02-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="47d02-190">O oposto também é verdade.</span><span class="sxs-lookup"><span data-stu-id="47d02-190">The opposite is true too.</span></span>

<span data-ttu-id="47d02-191">Para obter uma referência completa de sintaxe de Navalha, consulte [a referência de sintaxe de Navalha para ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="47d02-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="47d02-192">Usar componentes</span><span class="sxs-lookup"><span data-stu-id="47d02-192">Use components</span></span>

<span data-ttu-id="47d02-193">Além do HTML normal, os componentes também podem usar outros componentes como parte de sua lógica de renderização.</span><span class="sxs-lookup"><span data-stu-id="47d02-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="47d02-194">A sintaxe para usar um componente no Razor é semelhante ao uso de um controle de usuário em um aplicativo ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="47d02-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="47d02-195">Os componentes são especificados usando uma tag de elemento que corresponde ao nome do tipo do componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="47d02-196">Por exemplo, você `Counter` pode adicionar um componente como este:</span><span class="sxs-lookup"><span data-stu-id="47d02-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="47d02-197">Ao contrário ASP.NET Formulários web, componentes em Blazor:</span><span class="sxs-lookup"><span data-stu-id="47d02-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="47d02-198">Não use um prefixo de `asp:`elemento (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="47d02-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="47d02-199">Não é necessário registro na página ou na *web.config*.</span><span class="sxs-lookup"><span data-stu-id="47d02-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="47d02-200">Pense em componentes razor como você faria .NET tipos, porque isso é exatamente o que eles são.</span><span class="sxs-lookup"><span data-stu-id="47d02-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="47d02-201">Se o conjunto que contém o componente for referenciado, o componente está disponível para uso.</span><span class="sxs-lookup"><span data-stu-id="47d02-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="47d02-202">Para colocar o namespace do componente `@using` no escopo, aplique a diretiva:</span><span class="sxs-lookup"><span data-stu-id="47d02-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="47d02-203">Como visto nos projetos padrão do Blazor, `@using` é comum colocar diretivas em um arquivo *_Imports.razor* para que sejam importados em todos os arquivos *.razor* no mesmo diretório e em diretórios infantis.</span><span class="sxs-lookup"><span data-stu-id="47d02-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="47d02-204">Se o namespace de um componente não estiver no escopo, você poderá especificar um componente usando seu nome de tipo completo, como você pode em C#:</span><span class="sxs-lookup"><span data-stu-id="47d02-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="47d02-205">Parâmetros do componente</span><span class="sxs-lookup"><span data-stu-id="47d02-205">Component parameters</span></span>

<span data-ttu-id="47d02-206">Em ASP.NET Formulários da Web, você pode fluir parâmetros e dados para controles usando propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="47d02-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="47d02-207">Essas propriedades podem ser definidas na marcação usando atributos ou definidas diretamente em código.</span><span class="sxs-lookup"><span data-stu-id="47d02-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="47d02-208">Os componentes blazor funcionam de forma semelhante, embora as `[Parameter]` propriedades dos componentes também devem ser marcadas com o atributo a ser considerado parâmetros componentes.</span><span class="sxs-lookup"><span data-stu-id="47d02-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="47d02-209">O `Counter` componente a seguir define `IncrementAmount` um parâmetro de componente chamado `Counter` que pode ser usado para especificar a quantidade que deve ser incrementada cada vez que o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="47d02-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="47d02-210">Para especificar um parâmetro de componente no Blazor, use um atributo como você faria em ASP.NET Formulários da Web:</span><span class="sxs-lookup"><span data-stu-id="47d02-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="47d02-211">Manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="47d02-211">Event handlers</span></span>

<span data-ttu-id="47d02-212">Ambos ASP.NET Web Forms e Blazor fornecem um modelo de programação baseado em eventos para lidar com eventos de IA.</span><span class="sxs-lookup"><span data-stu-id="47d02-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="47d02-213">Exemplos de tais eventos incluem cliques de botão e entrada de texto.</span><span class="sxs-lookup"><span data-stu-id="47d02-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="47d02-214">Em ASP.NET Formulários da Web, você usa controles de servidor HTML para lidar com eventos de IU expostos pelo DOM ou pode lidar com eventos expostos por controles de servidor web.</span><span class="sxs-lookup"><span data-stu-id="47d02-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="47d02-215">Os eventos são divulgados no servidor através de solicitações pós-retorno.</span><span class="sxs-lookup"><span data-stu-id="47d02-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="47d02-216">Considere o seguinte exemplo de clique no botão Formulários da Web:</span><span class="sxs-lookup"><span data-stu-id="47d02-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="47d02-217">*Counter.ascx*</span><span class="sxs-lookup"><span data-stu-id="47d02-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="47d02-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="47d02-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="47d02-219">Em Blazor, você pode registrar manipuladores para eventos DOM UI diretamente usando atributos diretivos do formulário `@on{event}`.</span><span class="sxs-lookup"><span data-stu-id="47d02-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="47d02-220">O `{event}` espaço reservado representa o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="47d02-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="47d02-221">Por exemplo, você pode ouvir cliques de botão como este:</span><span class="sxs-lookup"><span data-stu-id="47d02-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="47d02-222">Os manipuladores de eventos podem aceitar um argumento opcional específico do evento para fornecer mais informações sobre o evento.</span><span class="sxs-lookup"><span data-stu-id="47d02-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="47d02-223">Por exemplo, eventos de `MouseEventArgs` mouse podem ter um argumento, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="47d02-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="47d02-224">Em vez de se referir a um grupo de métodos para um manipulador de eventos, você pode usar uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="47d02-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="47d02-225">Uma expressão lambda permite que você feche sobre outros valores no escopo.</span><span class="sxs-lookup"><span data-stu-id="47d02-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="47d02-226">Os manipuladores de eventos podem executar de forma sincronizada ou assíncrona.</span><span class="sxs-lookup"><span data-stu-id="47d02-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="47d02-227">Por exemplo, `OnClick` o seguinte manipulador de eventos é executado de forma assíncrona:</span><span class="sxs-lookup"><span data-stu-id="47d02-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="47d02-228">Depois que um evento é tratado, o componente é renderizado para explicar quaisquer alterações de estado de componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="47d02-229">Com manipuladores de eventos assíncronos, o componente é renderizado imediatamente após a execução do manipulador ser concluída.</span><span class="sxs-lookup"><span data-stu-id="47d02-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="47d02-230">O componente é renderizado *novamente* após `Task` a conclusão assíncrona.</span><span class="sxs-lookup"><span data-stu-id="47d02-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="47d02-231">Este modo de execução assíncrona oferece uma oportunidade de `Task` renderizar alguma ui apropriada enquanto o assíncrono ainda está em andamento.</span><span class="sxs-lookup"><span data-stu-id="47d02-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

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

<span data-ttu-id="47d02-232">Os componentes também podem definir seus próprios `EventCallback<TValue>`eventos definindo um parâmetro componente do tipo .</span><span class="sxs-lookup"><span data-stu-id="47d02-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="47d02-233">Os retornos de eventos suportam todas as variações dos manipuladores de eventos DOM UI: argumentos opcionais, grupos de métodos síncronos ou assíncronos ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="47d02-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="47d02-234">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="47d02-234">Data binding</span></span>

<span data-ttu-id="47d02-235">O Blazor fornece um mecanismo simples para vincular dados de um componente de interface do reino ao estado do componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="47d02-236">Essa abordagem difere dos recursos do ASP.NET Formulários da Web para vincular dados de fontes de dados a controles de IA.</span><span class="sxs-lookup"><span data-stu-id="47d02-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="47d02-237">Abordaremos o tratamento de dados de diferentes fontes de dados na [seção Lidar com dados.](data.md)</span><span class="sxs-lookup"><span data-stu-id="47d02-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="47d02-238">Para criar uma vinculação de dados bidirecionais de um componente `@bind` de UI ao estado do componente, use o atributo diretiva.</span><span class="sxs-lookup"><span data-stu-id="47d02-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="47d02-239">No exemplo a seguir, o valor da `isChecked` caixa de seleção está vinculado ao campo.</span><span class="sxs-lookup"><span data-stu-id="47d02-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="47d02-240">Quando o componente é renderizado, o valor da caixa `isChecked` de seleção é definido para o valor do campo.</span><span class="sxs-lookup"><span data-stu-id="47d02-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="47d02-241">Quando o usuário alterna a caixa `onchange` de seleção, o evento é acionado e o `isChecked` campo é definido como novo valor.</span><span class="sxs-lookup"><span data-stu-id="47d02-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="47d02-242">A `@bind` sintaxe neste caso é equivalente à seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="47d02-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="47d02-243">Para alterar o evento usado para `@bind:event` o bind, use o atributo.</span><span class="sxs-lookup"><span data-stu-id="47d02-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="47d02-244">Os componentes também podem suportar a vinculação de dados aos seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="47d02-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="47d02-245">Para vincular os dados, defina um parâmetro de retorno de chamada de evento com o mesmo nome do parâmetro vinculável.</span><span class="sxs-lookup"><span data-stu-id="47d02-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="47d02-246">O sufixo "Alterado" é adicionado ao nome.</span><span class="sxs-lookup"><span data-stu-id="47d02-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="47d02-247">*PasswordBox.razor*</span><span class="sxs-lookup"><span data-stu-id="47d02-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="47d02-248">Para acorrentar uma vinculação de dados a um elemento de ia de ia subjacente, defina o valor e manuseie o evento diretamente no elemento de IA em vez de usar o atributo. `@bind`</span><span class="sxs-lookup"><span data-stu-id="47d02-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="47d02-249">Para vincular a um parâmetro `@bind-{Parameter}` de componente, use um atributo para especificar o parâmetro ao qual deseja vincular.</span><span class="sxs-lookup"><span data-stu-id="47d02-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="47d02-250">Alterações de estado</span><span class="sxs-lookup"><span data-stu-id="47d02-250">State changes</span></span>

<span data-ttu-id="47d02-251">Se o estado do componente tiver sido alterado fora de um evento normal de ui ou retorno de evento, então o componente deve sinalizar manualmente que ele precisa ser renderizado novamente.</span><span class="sxs-lookup"><span data-stu-id="47d02-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="47d02-252">Para sinalizar que o estado de um `StateHasChanged` componente foi alterado, chame o método no componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="47d02-253">No exemplo abaixo, um componente exibe `AppState` uma mensagem de um serviço que pode ser atualizada por outras partes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47d02-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="47d02-254">O componente registra `StateHasChanged` seu `AppState.OnChange` método com o evento para que o componente seja renderizado sempre que a mensagem for atualizada.</span><span class="sxs-lookup"><span data-stu-id="47d02-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

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

## <a name="component-lifecycle"></a><span data-ttu-id="47d02-255">Ciclo de vida dos componentes</span><span class="sxs-lookup"><span data-stu-id="47d02-255">Component lifecycle</span></span>

<span data-ttu-id="47d02-256">A estrutura ASP.NET Formulários da Web tem métodos de ciclo de vida bem definidos para módulos, páginas e controles.</span><span class="sxs-lookup"><span data-stu-id="47d02-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="47d02-257">Por exemplo, o controle a seguir `Init`implementa manipuladores de eventos para os eventos do `Load`ciclo de vida e `UnLoad` do ciclo de vida:</span><span class="sxs-lookup"><span data-stu-id="47d02-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="47d02-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="47d02-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="47d02-259">Os componentes Blazor também têm um ciclo de vida bem definido.</span><span class="sxs-lookup"><span data-stu-id="47d02-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="47d02-260">O ciclo de vida de um componente pode ser usado para inicializar o estado do componente e implementar comportamentos componentes avançados.</span><span class="sxs-lookup"><span data-stu-id="47d02-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="47d02-261">Todos os métodos de ciclo de vida componentes de Blazor têm versões síncronas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="47d02-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="47d02-262">A renderização do componente é síncrona.</span><span class="sxs-lookup"><span data-stu-id="47d02-262">Component rendering is synchronous.</span></span> <span data-ttu-id="47d02-263">Você não pode executar lógica assíncrona como parte da renderização do componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="47d02-264">Toda lógica assíncrona deve `async` ser executada como parte de um método de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="47d02-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="47d02-265">Oninitialized</span><span class="sxs-lookup"><span data-stu-id="47d02-265">OnInitialized</span></span>

<span data-ttu-id="47d02-266">Os `OnInitialized` `OnInitializedAsync` métodos são usados para inicializar o componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="47d02-267">Um componente é tipicamente inicializado após a primeira renderização.</span><span class="sxs-lookup"><span data-stu-id="47d02-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="47d02-268">Depois que um componente é inicializado, ele pode ser renderizado várias vezes antes de ser eventualmente descartado.</span><span class="sxs-lookup"><span data-stu-id="47d02-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="47d02-269">O `OnInitialized` método é `Page_Load` semelhante ao evento em ASP.NET páginas e controles da Web Forms.</span><span class="sxs-lookup"><span data-stu-id="47d02-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="47d02-270">Conjunto de parâmetros</span><span class="sxs-lookup"><span data-stu-id="47d02-270">OnParametersSet</span></span>

<span data-ttu-id="47d02-271">Os `OnParametersSet` `OnParametersSetAsync` métodos são chamados quando um componente recebe parâmetros de seu pai e o valor é atribuído às propriedades.</span><span class="sxs-lookup"><span data-stu-id="47d02-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="47d02-272">Esses métodos são executados após a inicialização do componente e *cada vez que o componente é renderizado*.</span><span class="sxs-lookup"><span data-stu-id="47d02-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="47d02-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="47d02-273">OnAfterRender</span></span>

<span data-ttu-id="47d02-274">Os `OnAfterRender` `OnAfterRenderAsync` métodos são chamados depois que um componente termina a renderização.</span><span class="sxs-lookup"><span data-stu-id="47d02-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="47d02-275">As referências de elementos e componentes são preenchidas neste ponto (mais sobre esses conceitos abaixo).</span><span class="sxs-lookup"><span data-stu-id="47d02-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="47d02-276">A interatividade com o navegador está ativada neste momento.</span><span class="sxs-lookup"><span data-stu-id="47d02-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="47d02-277">Interações com a execução do DOM e JavaScript podem ocorrer com segurança.</span><span class="sxs-lookup"><span data-stu-id="47d02-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="47d02-278">`OnAfterRender`e `OnAfterRenderAsync` *não são chamados ao pré-renderização no servidor*.</span><span class="sxs-lookup"><span data-stu-id="47d02-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="47d02-279">O `firstRender` parâmetro `true` é a primeira vez que o componente é renderizado; caso contrário, seu `false`valor é .</span><span class="sxs-lookup"><span data-stu-id="47d02-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="47d02-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="47d02-280">IDisposable</span></span>

<span data-ttu-id="47d02-281">Os componentes Blazor podem ser implementados `IDisposable` para eliminar os recursos quando o componente é removido da ui.</span><span class="sxs-lookup"><span data-stu-id="47d02-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="47d02-282">Um componente Razor `IDispose` pode `@implements` ser implementado usando a diretiva:</span><span class="sxs-lookup"><span data-stu-id="47d02-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="47d02-283">Capturar referências de componentes</span><span class="sxs-lookup"><span data-stu-id="47d02-283">Capture component references</span></span>

<span data-ttu-id="47d02-284">Em ASP.NET Formulários da Web, é comum manipular uma instância de controle diretamente no código, referindo-se ao seu ID.</span><span class="sxs-lookup"><span data-stu-id="47d02-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="47d02-285">Em Blazor, também é possível capturar e manipular uma referência a um componente, embora seja muito menos comum.</span><span class="sxs-lookup"><span data-stu-id="47d02-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="47d02-286">Para capturar uma referência de componente `@ref` em Blazor, use o atributo diretivo.</span><span class="sxs-lookup"><span data-stu-id="47d02-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="47d02-287">O valor do atributo deve corresponder ao nome de um campo settable com o mesmo tipo do componente referenciado.</span><span class="sxs-lookup"><span data-stu-id="47d02-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="47d02-288">Quando o componente pai é renderizado, o campo é preenchido com a instância do componente filho.</span><span class="sxs-lookup"><span data-stu-id="47d02-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="47d02-289">Em seguida, você pode chamar métodos ou manipular a instância do componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="47d02-290">A manipulação do estado do componente diretamente usando referências de componentes não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="47d02-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="47d02-291">Isso evita que o componente seja renderizado automaticamente nos horários corretos.</span><span class="sxs-lookup"><span data-stu-id="47d02-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="47d02-292">Referências de elemento de captura</span><span class="sxs-lookup"><span data-stu-id="47d02-292">Capture element references</span></span>

<span data-ttu-id="47d02-293">Os componentes blazor podem capturar referências a um elemento.</span><span class="sxs-lookup"><span data-stu-id="47d02-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="47d02-294">Ao contrário dos controles de servidor HTML em ASP.NET Formulários da Web, você não pode manipular o DOM diretamente usando uma referência de elemento no Blazor.</span><span class="sxs-lookup"><span data-stu-id="47d02-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="47d02-295">Blazor lida com a maioria das interações DOM para você usando seu algoritmo de difusão DOM.</span><span class="sxs-lookup"><span data-stu-id="47d02-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="47d02-296">As referências de elementos capturados em Blazor são opacas.</span><span class="sxs-lookup"><span data-stu-id="47d02-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="47d02-297">No entanto, eles são usados para passar uma referência de elemento específico em uma chamada interop JavaScript.</span><span class="sxs-lookup"><span data-stu-id="47d02-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="47d02-298">Para obter mais informações sobre o Interop JavaScript, consulte [ASP.NET interop Core Blazor JavaScript](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="47d02-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="47d02-299">Componentes modelados</span><span class="sxs-lookup"><span data-stu-id="47d02-299">Templated components</span></span>

<span data-ttu-id="47d02-300">Em ASP.NET Formulários da Web, você pode criar *controles modelados.*</span><span class="sxs-lookup"><span data-stu-id="47d02-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="47d02-301">Os controles modelados permitem que o desenvolvedor especifique uma parte do HTML usado para renderizar um controle de contêiner.</span><span class="sxs-lookup"><span data-stu-id="47d02-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="47d02-302">A mecânica de construir controles de servidor modelados é complexa, mas permite cenários poderosos para renderização de dados de forma personalizável do usuário.</span><span class="sxs-lookup"><span data-stu-id="47d02-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="47d02-303">Exemplos de controles modelados incluem `Repeater` e `DataList`.</span><span class="sxs-lookup"><span data-stu-id="47d02-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="47d02-304">Os componentes Blazor também podem ser modelados definindo parâmetros de componentes do tipo `RenderFragment` ou `RenderFragment<T>`.</span><span class="sxs-lookup"><span data-stu-id="47d02-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="47d02-305">A `RenderFragment` representa um pedaço de marcação Razor que pode então ser renderizado pelo componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="47d02-306">A `RenderFragment<T>` é um pedaço de marcação razor que leva um parâmetro que pode ser especificado quando o fragmento de renderização é renderizado.</span><span class="sxs-lookup"><span data-stu-id="47d02-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="47d02-307">Conteúdo infantil</span><span class="sxs-lookup"><span data-stu-id="47d02-307">Child content</span></span>

<span data-ttu-id="47d02-308">Os componentes Blazor podem capturar `RenderFragment` seu conteúdo infantil como um e renderizar esse conteúdo como parte da renderização do componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="47d02-309">Para capturar o conteúdo do filho, `RenderFragment` defina `ChildContent`um parâmetro de componente de tipo e nomeie-o .</span><span class="sxs-lookup"><span data-stu-id="47d02-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="47d02-310">*ChildContentComponent.razor*</span><span class="sxs-lookup"><span data-stu-id="47d02-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="47d02-311">Um componente pai pode, então, fornecer conteúdo infantil usando sintaxe de navalha normal.</span><span class="sxs-lookup"><span data-stu-id="47d02-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="47d02-312">Parâmetros de modelo</span><span class="sxs-lookup"><span data-stu-id="47d02-312">Template parameters</span></span>

<span data-ttu-id="47d02-313">Um componente Blazor modelado também pode `RenderFragment` `RenderFragment<T>`definir vários parâmetros de componentes do tipo ou .</span><span class="sxs-lookup"><span data-stu-id="47d02-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="47d02-314">O parâmetro para `RenderFragment<T>` um pode ser especificado quando é invocado.</span><span class="sxs-lookup"><span data-stu-id="47d02-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="47d02-315">Para especificar um parâmetro de tipo `@typeparam` genérico para um componente, use a diretiva Razor.</span><span class="sxs-lookup"><span data-stu-id="47d02-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="47d02-316">*SimpleListView.razor*</span><span class="sxs-lookup"><span data-stu-id="47d02-316">*SimpleListView.razor*</span></span>

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

<span data-ttu-id="47d02-317">Ao usar um componente modelado, os parâmetros do modelo podem ser especificados usando elementos infantis que correspondem aos nomes dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="47d02-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="47d02-318">Argumentos componentes `RenderFragment<T>` do tipo passados como `context`elementos têm um parâmetro implícito chamado .</span><span class="sxs-lookup"><span data-stu-id="47d02-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="47d02-319">Você pode alterar o nome deste `Context` parâmetro de implemento usando o atributo no elemento filho.</span><span class="sxs-lookup"><span data-stu-id="47d02-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="47d02-320">Quaisquer parâmetros de tipo genéricos podem ser especificados usando um atributo que corresponda ao nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="47d02-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="47d02-321">O parâmetro de tipo será inferido se possível:</span><span class="sxs-lookup"><span data-stu-id="47d02-321">The type parameter will be inferred if possible:</span></span>

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

<span data-ttu-id="47d02-322">A saída deste componente é assim:</span><span class="sxs-lookup"><span data-stu-id="47d02-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="47d02-323">Code-behind</span><span class="sxs-lookup"><span data-stu-id="47d02-323">Code-behind</span></span>

<span data-ttu-id="47d02-324">Um componente Blazor é tipicamente de autoria em um único *arquivo .razor.*</span><span class="sxs-lookup"><span data-stu-id="47d02-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="47d02-325">No entanto, também é possível separar o código e a marcação usando um arquivo de código atrás.</span><span class="sxs-lookup"><span data-stu-id="47d02-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="47d02-326">Para usar um arquivo de componente, adicione um arquivo C# que corresponda ao nome do arquivo do arquivo componente, mas com uma extensão *.cs* adicionada *(Counter.razor.cs).*</span><span class="sxs-lookup"><span data-stu-id="47d02-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="47d02-327">Use o arquivo C# para definir uma classe base para o componente.</span><span class="sxs-lookup"><span data-stu-id="47d02-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="47d02-328">Você pode nomear a classe base o que quiser, mas é comum nomear a classe `Base` como`CounterBase`a classe componente, mas com uma extensão adicionada ( ).</span><span class="sxs-lookup"><span data-stu-id="47d02-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="47d02-329">A classe baseada em componentes também deve derivar de `ComponentBase`.</span><span class="sxs-lookup"><span data-stu-id="47d02-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="47d02-330">Em seguida, no arquivo de `@inherits` componente Razor, adicione a`@inherits CounterBase`diretiva para especificar a classe base para o componente ( ).</span><span class="sxs-lookup"><span data-stu-id="47d02-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="47d02-331">*Contador.navalha*</span><span class="sxs-lookup"><span data-stu-id="47d02-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="47d02-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="47d02-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="47d02-333">A visibilidade dos membros do componente na classe `protected` `public` base deve ser ou visível para a classe de componentes.</span><span class="sxs-lookup"><span data-stu-id="47d02-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="47d02-334">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="47d02-334">Additional resources</span></span>

<span data-ttu-id="47d02-335">O precedente não é um tratamento exaustivo de todos os aspectos dos componentes blazor.</span><span class="sxs-lookup"><span data-stu-id="47d02-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="47d02-336">Para obter mais informações sobre como [criar e usar ASP.NET componentes do Core Razor,](/aspnet/core/blazor/components)consulte a documentação blazor.</span><span class="sxs-lookup"><span data-stu-id="47d02-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="47d02-337">[Próximo](app-startup.md)
>[anterior](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="47d02-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
