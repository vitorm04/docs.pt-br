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
# <a name="build-reusable-ui-components-with-blazor"></a>Construa componentes de IU reutilizáveis com Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Uma das coisas bonitas sobre ASP.NET Web Forms é como ele permite o encapsulamento de peças reutilizáveis do código de interface do usuário (UI) em controles de interface do usuário reutilizáveis. Controles personalizados do usuário podem ser definidos em marcação usando arquivos *.ascx.* Você também pode construir controles de servidor elaborados em código com suporte completo ao designer.

Blazor também suporta encapsulamento de IU através de *componentes*. Um componente:

- É um pedaço independente de ui.
- Mantém seu próprio estado e lógica de renderização.
- Pode definir manipuladores de eventos de ui, vincular-se a dados de entrada e gerenciar seu próprio ciclo de vida.
- É tipicamente definido em um arquivo *.razor* usando sintaxe de navalha.

## <a name="an-introduction-to-razor"></a>Uma introdução a Razor

Razor é uma linguagem de marcação leve baseada em HTML e C#. Com razor, você pode fazer uma transição perfeita entre o código de marcação e c# para definir sua lógica de renderização de componentes. Quando o arquivo *.razor* é compilado, a lógica de renderização é capturada de forma estruturada em uma classe .NET. O nome da classe compilada é retirado do nome do arquivo *.razor.* O namespace é retirado do namespace padrão para o projeto e o caminho da `@namespace` pasta, ou você pode especificar explicitamente o namespace usando a diretiva (mais em diretivas de Navalha abaixo).

A lógica de renderização de um componente é de autoria usando marcação HTML normal com lógica dinâmica adicionada usando C#. O `@` personagem é usado para fazer a transição para C#. Razor é tipicamente inteligente em descobrir quando você mudou de volta para HTML. Por exemplo, o seguinte `<p>` componente renderiza uma tag com o tempo atual:

```razor
<p>@DateTime.Now</p>
```

Para especificar explicitamente o início e o fim de uma expressão C#, use parênteses:

```razor
<p>@(DateTime.Now)</p>
```

Razor também facilita o uso do fluxo de controle C# em sua lógica de renderização. Por exemplo, você pode condicionalmente renderizar alguns HTML como este:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Ou você pode gerar uma lista de itens `foreach` usando um loop C# normal como este:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

As diretivas de navalha, como as diretivas em ASP.NET Formulários da Web, controlam muitos aspectos de como um componente Razor é compilado. Exemplos incluem os componentes:

- Namespace
- Classe base
- Interfaces implementadas
- Parâmetros genéricos
- Namespaces importados
- Rotas

As diretivas de `@` navalha começam com o caractere e são normalmente usadas no início de uma nova linha no início do arquivo. Por exemplo, `@namespace` a diretiva define o espaço de nome do componente:

```razor
@namespace MyComponentNamespace
```

A tabela a seguir resume as várias diretivas de Navalha usadas em Blazor e seus ASP.NET equivalentes web forms, se existirem.

|Diretiva    |Descrição|Exemplo|Formulários web equivalentes|
|-------------|-----------|-------|--------------------|
|`@attribute` |Adiciona um atributo de nível de classe ao componente|`@attribute [Authorize]`|Nenhum|
|`@code`      |Adiciona membros da classe ao componente|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implementa a interface especificada|`@implements IDisposable`|Usar code-behind|
|`@inherits`  |Herda da classe base especificada|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Injeta um serviço no componente|`@inject IJSRuntime JS`|Nenhum|
|`@layout`    |Especifica um componente de layout para o componente|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Define o namespace para o componente|`@namespace MyNamespace`|Nenhum|
|`@page`      |Especifica a rota para o componente|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Especifica um parâmetro de tipo genérico para o componente|`@typeparam TItem`|Usar code-behind|
|`@using`     |Especifica um namespace para trazer para o escopo|`@using MyComponentNamespace`|Adicionar namespace em *web.config*|

Os componentes da navalha também fazem uso extensivo de *atributos de diretiva sobre elementos* para controlar vários aspectos de como os componentes são compilados (manipulação de eventos, vinculação de dados, referências de elementos & componentes, e assim por diante). Todos os atributos diretivos seguem uma sintaxe genérica comum onde os valores entre parênteses são opcionais:

```razor
@directive(-suffix(:name))(="value")
```

A tabela a seguir resume os vários atributos para as diretivas de Razor usadas em Blazor.

|Atributo    |Descrição|Exemplo|
|-------------|-----------|-------|
|`@attributes`|Torna um dicionário de atributos|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Cria uma vinculação de dados bidirecional    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Adiciona um manipulador de eventos para o evento especificado|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Especifica uma chave a ser usada pelo algoritmo de difusão para preservar elementos em uma coleção|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Captura uma referência ao componente ou elemento HTML|`<MyDialog @ref="myDialog" />`|

Os vários atributos diretivos `@bind` `@ref`utilizados por Blazor (`@onclick`, , e assim por diante) são cobertos nas seções abaixo e capítulos posteriores.

Muitas das sintaxe usadas em arquivos *.aspx* e *.ascx* têm sintaxes paralelas em Razor. Abaixo está uma simples comparação das sintaxes para ASP.NET Formulários web e navalha.

|Recurso                      |Formulários da Web           |Sintaxe               |Razor         |Sintaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Diretivas                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Blocos de códigos                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Expressões<br>(CODIFICAdo em HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Implícita:`@`<br>Explícita:`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Comentários                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Associação de dados                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Para adicionar membros à classe de `@code` componentes Razor, use a diretiva. Essa técnica é semelhante `<script runat="server">...</script>` ao uso de um bloco em um ASP.NET o controle ou página do usuário do Web Forms.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Como razor é baseado em C#, ele deve ser compilado a partir de um projeto C# (*.csproj*). Você não pode compilar *arquivos .razor* de um projeto Visual Basic (*.vbproj*). Você ainda pode referenciar projetos Visual Basic do seu projeto Blazor. O oposto também é verdade.

Para obter uma referência completa de sintaxe de Navalha, consulte [a referência de sintaxe de Navalha para ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Usar componentes

Além do HTML normal, os componentes também podem usar outros componentes como parte de sua lógica de renderização. A sintaxe para usar um componente no Razor é semelhante ao uso de um controle de usuário em um aplicativo ASP.NET Web Forms. Os componentes são especificados usando uma tag de elemento que corresponde ao nome do tipo do componente. Por exemplo, você `Counter` pode adicionar um componente como este:

```razor
<Counter />
```

Ao contrário ASP.NET Formulários web, componentes em Blazor:

- Não use um prefixo de `asp:`elemento (por exemplo, ).
- Não é necessário registro na página ou na *web.config*.

Pense em componentes razor como você faria .NET tipos, porque isso é exatamente o que eles são. Se o conjunto que contém o componente for referenciado, o componente está disponível para uso. Para colocar o namespace do componente `@using` no escopo, aplique a diretiva:

```razor
@using MyComponentLib

<Counter />
```

Como visto nos projetos padrão do Blazor, `@using` é comum colocar diretivas em um arquivo *_Imports.razor* para que sejam importados em todos os arquivos *.razor* no mesmo diretório e em diretórios infantis.

Se o namespace de um componente não estiver no escopo, você poderá especificar um componente usando seu nome de tipo completo, como você pode em C#:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Parâmetros do componente

Em ASP.NET Formulários da Web, você pode fluir parâmetros e dados para controles usando propriedades públicas. Essas propriedades podem ser definidas na marcação usando atributos ou definidas diretamente em código. Os componentes blazor funcionam de forma semelhante, embora as `[Parameter]` propriedades dos componentes também devem ser marcadas com o atributo a ser considerado parâmetros componentes.

O `Counter` componente a seguir define `IncrementAmount` um parâmetro de componente chamado `Counter` que pode ser usado para especificar a quantidade que deve ser incrementada cada vez que o botão é clicado.

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

Para especificar um parâmetro de componente no Blazor, use um atributo como você faria em ASP.NET Formulários da Web:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Manipuladores de eventos

Ambos ASP.NET Web Forms e Blazor fornecem um modelo de programação baseado em eventos para lidar com eventos de IA. Exemplos de tais eventos incluem cliques de botão e entrada de texto. Em ASP.NET Formulários da Web, você usa controles de servidor HTML para lidar com eventos de IU expostos pelo DOM ou pode lidar com eventos expostos por controles de servidor web. Os eventos são divulgados no servidor através de solicitações pós-retorno. Considere o seguinte exemplo de clique no botão Formulários da Web:

*Counter.ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

Em Blazor, você pode registrar manipuladores para eventos DOM UI diretamente usando atributos diretivos do formulário `@on{event}`. O `{event}` espaço reservado representa o nome do evento. Por exemplo, você pode ouvir cliques de botão como este:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Os manipuladores de eventos podem aceitar um argumento opcional específico do evento para fornecer mais informações sobre o evento. Por exemplo, eventos de `MouseEventArgs` mouse podem ter um argumento, mas não é necessário.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Em vez de se referir a um grupo de métodos para um manipulador de eventos, você pode usar uma expressão lambda. Uma expressão lambda permite que você feche sobre outros valores no escopo.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Os manipuladores de eventos podem executar de forma sincronizada ou assíncrona. Por exemplo, `OnClick` o seguinte manipulador de eventos é executado de forma assíncrona:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Depois que um evento é tratado, o componente é renderizado para explicar quaisquer alterações de estado de componente. Com manipuladores de eventos assíncronos, o componente é renderizado imediatamente após a execução do manipulador ser concluída. O componente é renderizado *novamente* após `Task` a conclusão assíncrona. Este modo de execução assíncrona oferece uma oportunidade de `Task` renderizar alguma ui apropriada enquanto o assíncrono ainda está em andamento.

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

Os componentes também podem definir seus próprios `EventCallback<TValue>`eventos definindo um parâmetro componente do tipo . Os retornos de eventos suportam todas as variações dos manipuladores de eventos DOM UI: argumentos opcionais, grupos de métodos síncronos ou assíncronos ou expressões lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Associação de dados

O Blazor fornece um mecanismo simples para vincular dados de um componente de interface do reino ao estado do componente. Essa abordagem difere dos recursos do ASP.NET Formulários da Web para vincular dados de fontes de dados a controles de IA. Abordaremos o tratamento de dados de diferentes fontes de dados na [seção Lidar com dados.](data.md)

Para criar uma vinculação de dados bidirecionais de um componente `@bind` de UI ao estado do componente, use o atributo diretiva. No exemplo a seguir, o valor da `isChecked` caixa de seleção está vinculado ao campo.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Quando o componente é renderizado, o valor da caixa `isChecked` de seleção é definido para o valor do campo. Quando o usuário alterna a caixa `onchange` de seleção, o evento é acionado e o `isChecked` campo é definido como novo valor. A `@bind` sintaxe neste caso é equivalente à seguinte marcação:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Para alterar o evento usado para `@bind:event` o bind, use o atributo.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Os componentes também podem suportar a vinculação de dados aos seus parâmetros. Para vincular os dados, defina um parâmetro de retorno de chamada de evento com o mesmo nome do parâmetro vinculável. O sufixo "Alterado" é adicionado ao nome.

*PasswordBox.razor*

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

Para acorrentar uma vinculação de dados a um elemento de ia de ia subjacente, defina o valor e manuseie o evento diretamente no elemento de IA em vez de usar o atributo. `@bind`

Para vincular a um parâmetro `@bind-{Parameter}` de componente, use um atributo para especificar o parâmetro ao qual deseja vincular.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Alterações de estado

Se o estado do componente tiver sido alterado fora de um evento normal de ui ou retorno de evento, então o componente deve sinalizar manualmente que ele precisa ser renderizado novamente. Para sinalizar que o estado de um `StateHasChanged` componente foi alterado, chame o método no componente.

No exemplo abaixo, um componente exibe `AppState` uma mensagem de um serviço que pode ser atualizada por outras partes do aplicativo. O componente registra `StateHasChanged` seu `AppState.OnChange` método com o evento para que o componente seja renderizado sempre que a mensagem for atualizada.

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

## <a name="component-lifecycle"></a>Ciclo de vida dos componentes

A estrutura ASP.NET Formulários da Web tem métodos de ciclo de vida bem definidos para módulos, páginas e controles. Por exemplo, o controle a seguir `Init`implementa manipuladores de eventos para os eventos do `Load`ciclo de vida e `UnLoad` do ciclo de vida:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Os componentes Blazor também têm um ciclo de vida bem definido. O ciclo de vida de um componente pode ser usado para inicializar o estado do componente e implementar comportamentos componentes avançados.

Todos os métodos de ciclo de vida componentes de Blazor têm versões síncronas e assíncronas. A renderização do componente é síncrona. Você não pode executar lógica assíncrona como parte da renderização do componente. Toda lógica assíncrona deve `async` ser executada como parte de um método de ciclo de vida.

### <a name="oninitialized"></a>Oninitialized

Os `OnInitialized` `OnInitializedAsync` métodos são usados para inicializar o componente. Um componente é tipicamente inicializado após a primeira renderização. Depois que um componente é inicializado, ele pode ser renderizado várias vezes antes de ser eventualmente descartado. O `OnInitialized` método é `Page_Load` semelhante ao evento em ASP.NET páginas e controles da Web Forms.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>Conjunto de parâmetros

Os `OnParametersSet` `OnParametersSetAsync` métodos são chamados quando um componente recebe parâmetros de seu pai e o valor é atribuído às propriedades. Esses métodos são executados após a inicialização do componente e *cada vez que o componente é renderizado*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Os `OnAfterRender` `OnAfterRenderAsync` métodos são chamados depois que um componente termina a renderização. As referências de elementos e componentes são preenchidas neste ponto (mais sobre esses conceitos abaixo). A interatividade com o navegador está ativada neste momento. Interações com a execução do DOM e JavaScript podem ocorrer com segurança.

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

`OnAfterRender`e `OnAfterRenderAsync` *não são chamados ao pré-renderização no servidor*.

O `firstRender` parâmetro `true` é a primeira vez que o componente é renderizado; caso contrário, seu `false`valor é .

### <a name="idisposable"></a>IDisposable

Os componentes Blazor podem ser implementados `IDisposable` para eliminar os recursos quando o componente é removido da ui. Um componente Razor `IDispose` pode `@implements` ser implementado usando a diretiva:

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

## <a name="capture-component-references"></a>Capturar referências de componentes

Em ASP.NET Formulários da Web, é comum manipular uma instância de controle diretamente no código, referindo-se ao seu ID. Em Blazor, também é possível capturar e manipular uma referência a um componente, embora seja muito menos comum.

Para capturar uma referência de componente `@ref` em Blazor, use o atributo diretivo. O valor do atributo deve corresponder ao nome de um campo settable com o mesmo tipo do componente referenciado.

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

Quando o componente pai é renderizado, o campo é preenchido com a instância do componente filho. Em seguida, você pode chamar métodos ou manipular a instância do componente.

A manipulação do estado do componente diretamente usando referências de componentes não é recomendada. Isso evita que o componente seja renderizado automaticamente nos horários corretos.

## <a name="capture-element-references"></a>Referências de elemento de captura

Os componentes blazor podem capturar referências a um elemento. Ao contrário dos controles de servidor HTML em ASP.NET Formulários da Web, você não pode manipular o DOM diretamente usando uma referência de elemento no Blazor. Blazor lida com a maioria das interações DOM para você usando seu algoritmo de difusão DOM. As referências de elementos capturados em Blazor são opacas. No entanto, eles são usados para passar uma referência de elemento específico em uma chamada interop JavaScript. Para obter mais informações sobre o Interop JavaScript, consulte [ASP.NET interop Core Blazor JavaScript](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Componentes modelados

Em ASP.NET Formulários da Web, você pode criar *controles modelados.* Os controles modelados permitem que o desenvolvedor especifique uma parte do HTML usado para renderizar um controle de contêiner. A mecânica de construir controles de servidor modelados é complexa, mas permite cenários poderosos para renderização de dados de forma personalizável do usuário. Exemplos de controles modelados incluem `Repeater` e `DataList`.

Os componentes Blazor também podem ser modelados definindo parâmetros de componentes do tipo `RenderFragment` ou `RenderFragment<T>`. A `RenderFragment` representa um pedaço de marcação Razor que pode então ser renderizado pelo componente. A `RenderFragment<T>` é um pedaço de marcação razor que leva um parâmetro que pode ser especificado quando o fragmento de renderização é renderizado.

### <a name="child-content"></a>Conteúdo infantil

Os componentes Blazor podem capturar `RenderFragment` seu conteúdo infantil como um e renderizar esse conteúdo como parte da renderização do componente. Para capturar o conteúdo do filho, `RenderFragment` defina `ChildContent`um parâmetro de componente de tipo e nomeie-o .

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Um componente pai pode, então, fornecer conteúdo infantil usando sintaxe de navalha normal.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Parâmetros de modelo

Um componente Blazor modelado também pode `RenderFragment` `RenderFragment<T>`definir vários parâmetros de componentes do tipo ou . O parâmetro para `RenderFragment<T>` um pode ser especificado quando é invocado. Para especificar um parâmetro de tipo `@typeparam` genérico para um componente, use a diretiva Razor.

*SimpleListView.razor*

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

Ao usar um componente modelado, os parâmetros do modelo podem ser especificados usando elementos infantis que correspondem aos nomes dos parâmetros. Argumentos componentes `RenderFragment<T>` do tipo passados como `context`elementos têm um parâmetro implícito chamado . Você pode alterar o nome deste `Context` parâmetro de implemento usando o atributo no elemento filho. Quaisquer parâmetros de tipo genéricos podem ser especificados usando um atributo que corresponda ao nome do parâmetro de tipo. O parâmetro de tipo será inferido se possível:

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

A saída deste componente é assim:

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Code-behind

Um componente Blazor é tipicamente de autoria em um único *arquivo .razor.* No entanto, também é possível separar o código e a marcação usando um arquivo de código atrás. Para usar um arquivo de componente, adicione um arquivo C# que corresponda ao nome do arquivo do arquivo componente, mas com uma extensão *.cs* adicionada *(Counter.razor.cs).* Use o arquivo C# para definir uma classe base para o componente. Você pode nomear a classe base o que quiser, mas é comum nomear a classe `Base` como`CounterBase`a classe componente, mas com uma extensão adicionada ( ). A classe baseada em componentes também deve derivar de `ComponentBase`. Em seguida, no arquivo de `@inherits` componente Razor, adicione a`@inherits CounterBase`diretiva para especificar a classe base para o componente ( ).

*Contador.navalha*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

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

A visibilidade dos membros do componente na classe `protected` `public` base deve ser ou visível para a classe de componentes.

## <a name="additional-resources"></a>Recursos adicionais

O precedente não é um tratamento exaustivo de todos os aspectos dos componentes blazor. Para obter mais informações sobre como [criar e usar ASP.NET componentes do Core Razor,](/aspnet/core/blazor/components)consulte a documentação blazor.

>[!div class="step-by-step"]
>[Próximo](app-startup.md)
>[anterior](pages-routing-layouts.md)
