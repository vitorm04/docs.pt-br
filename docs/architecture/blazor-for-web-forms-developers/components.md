---
title: Crie componentes de interface do usuário reutilizáveis com mais utilidade
description: Saiba como criar componentes de interface do usuário reutilizáveis com mais e como eles se comparam aos controles de Web Forms de ASP.NET.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 79919b183a4eb759f0b27c97500ee71c9378770b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088098"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Crie componentes de interface do usuário reutilizáveis com mais utilidade

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Uma das belas coisas sobre o ASP.NET Web Forms é como ela permite o encapsulamento de partes reutilizáveis do código da interface do usuário em controles de interface de usuários reutilizáveis. Os controles de usuário personalizados podem ser definidos na marcação usando arquivos *. ascx* . Você também pode criar controles de servidor elaborados em código com suporte completo ao designer.

Também dá suporte ao encapsulamento de interface do usuário por meio de *componentes*. Um componente:

- É uma parte independente da interface do usuário.
- Mantém seu próprio Estado e lógica de renderização.
- Pode definir manipuladores de eventos de interface do usuário, associar a dados de entrada e gerenciar seu próprio ciclo de vida.
- Normalmente é definido em um arquivo *. Razor* usando sintaxe Razor.

## <a name="an-introduction-to-razor"></a>Uma introdução ao Razor

O Razor é uma linguagem de modelagem de marcação leve com base em C#HTML e. Com o Razor, você pode fazer a transição diretamente entre C# a marcação e o código para definir a lógica de renderização do componente. Quando o arquivo *. Razor* é compilado, a lógica de renderização é capturada de forma estruturada em uma classe do .net. O nome da classe compilada é extraído do nome do arquivo *. Razor* . O namespace é extraído do namespace padrão para o projeto e o caminho da pasta, ou você pode especificar explicitamente o namespace usando a diretiva `@namespace` (mais sobre as diretivas do Razor abaixo).

A lógica de renderização de um componente é criada usando marcação HTML normal com lógica dinâmica adicionada C#usando. O caractere `@` é usado para fazer a C#transição para. O Razor normalmente é inteligente para descobrir quando você volta para o HTML. Por exemplo, o componente a seguir renderiza uma marca de `<p>` com a hora atual:

```razor
<p>@DateTime.Now</p>
```

Para especificar explicitamente o início e o final de C# uma expressão, use parênteses:

```razor
<p>@(DateTime.Now)</p>
```

O Razor também facilita o uso C# do fluxo de controle na lógica de renderização. Por exemplo, você pode renderizar condicionalmente um HTML como este:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Ou você pode gerar uma lista de itens usando um loop C# de `foreach` normal como este:

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

As diretivas do Razor, como diretivas no ASP.NET Web Forms, controlam muitos aspectos de como um componente Razor é compilado. Os exemplos incluem o componente:

- {1&gt;Namespace&lt;1}
- Classe base
- Interfaces implementadas
- Parâmetros genéricos
- Namespaces importados
- Rotas

As diretivas do Razor começam com o `@` caractere e são normalmente usadas no início de uma nova linha no início do arquivo. Por exemplo, a diretiva `@namespace` define o namespace do componente:

```razor
@namespace MyComponentNamespace
```

A tabela a seguir resume as várias diretivas Razor usadas no mais e suas ASP.NET Web Forms equivalentes, se existirem.

|Directive    |Descrição|{1&gt;Exemplo&lt;1}|Web Forms equivalente|
|-------------|-----------|-------|--------------------|
|`@attribute` |Adiciona um atributo de nível de classe ao componente|`@attribute [Authorize]`|Nenhum|
|`@code`      |Adiciona membros de classe ao componente|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implementa a interface especificada|`@implements IDisposable`|Usar code-behind|
|`@inherits`  |Herda da classe base especificada|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Injeta um serviço no componente|`@inject IJSRuntime JS`|Nenhum|
|`@layout`    |Especifica um componente de layout para o componente|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Define o namespace para o componente|`@namespace MyNamespace`|Nenhum|
|`@page`      |Especifica a rota para o componente|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Especifica um parâmetro de tipo genérico para o componente|`@typeparam TItem`|Usar code-behind|
|`@using`     |Especifica um namespace para trazer para o escopo|`@using MyComponentNamespace`|Adicionar namespace em *Web. config*|

Os componentes do Razor também fazem uso extensivo de *atributos de diretiva* em elementos para controlar vários aspectos de como os componentes são compilados (manipulação de eventos, vinculação de dados, referências de elementos de & de componentes e assim por diante). Atributos de diretiva seguem uma sintaxe genérica comum em que os valores entre parênteses são opcionais:

```razor
@directive(-suffix(:name))(="value")
```

A tabela a seguir resume os vários atributos para as diretivas do Razor usadas no mais incrivelmente.

|Atributo    |Descrição|{1&gt;Exemplo&lt;1}|
|-------------|-----------|-------|
|`@attributes`|Renderiza um dicionário de atributos|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Cria uma associação de dados bidirecional    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Adiciona um manipulador de eventos para o evento especificado|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Especifica uma chave a ser usada pelo algoritmo diff para preservar elementos em uma coleção|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Captura uma referência para o componente ou elemento HTML|`<MyDialog @ref="myDialog" />`|

Os vários atributos de diretiva usados pelo mais recente (`@onclick`, `@bind`, `@ref`e assim por diante) são abordados nas seções abaixo e nos capítulos posteriores.

Muitas das sintaxes usadas em arquivos *. aspx* e *. ascx* têm sintaxes paralelas no Razor. Veja abaixo uma comparação simples das sintaxes para ASP.NET Web Forms e Razor.

|Recurso                      |Web Forms           |Sintaxe               |Razor         |Sintaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Diretivas                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Blocos de código                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|{1&gt;Expressões&lt;1}<br>(Codificado em HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Implícito: `@`<br>Explícito: `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Comments                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Associação de dados                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Para adicionar membros à classe de componente Razor, use a diretiva `@code`. Essa técnica é semelhante ao uso de um bloco de `<script runat="server">...</script>` em uma página ou controle de usuário do ASP.NET Web Forms.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Como o Razor se baseia C#em, ele deve ser compilado de dentro C# de um projeto ( *. csproj*). Não é possível compilar arquivos *. Razor* de um projeto VB ( *. vbproj*). Você ainda pode fazer referência a projetos do VB por meio de seu projeto mais incrivelmente. O oposto também é verdadeiro.

Para obter uma referência completa de sintaxe Razor, consulte [referência de sintaxe Razor para ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Usar componentes

Além do HTML normal, os componentes também podem usar outros componentes como parte da lógica de renderização. A sintaxe para usar um componente no Razor é semelhante ao uso de um controle de usuário em um aplicativo ASP.NET Web Forms. Os componentes são especificados usando uma marca de elemento que corresponde ao nome do tipo do componente. Por exemplo, você pode adicionar um componente `Counter` como este:

```razor
<Counter />
```

Ao contrário de ASP.NET Web Forms, os componentes do mais incrivelmente:

- Não use um prefixo de elemento (por exemplo, `asp:`).
- Não exija o registro na página ou no *Web. config*.

Imagine os componentes do Razor como você faria com os tipos do .NET, pois isso é exatamente o que eles são. Se o assembly que contém o componente for referenciado, o componente estará disponível para uso. Para colocar o namespace do componente no escopo, aplique a diretiva `@using`:

```razor
@using MyComponentLib

<Counter />
```

Como visto nos projetos de mais de um padrão, é comum colocar `@using` diretivas em um arquivo *_Imports. Razor* para que elas sejam importadas para todos os arquivos *. Razor* no mesmo diretório e em diretórios filho.

Se o namespace de um componente não estiver no escopo, você poderá especificar um componente usando seu nome de tipo completo, como você C#pode:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Parâmetros do componente

No ASP.NET Web Forms, você pode fluir parâmetros e dados para controles usando propriedades públicas. Essas propriedades podem ser definidas na marcação usando atributos ou definidos diretamente no código. Os componentes mais úteis funcionam de maneira semelhante, embora as propriedades do componente também devam ser marcadas com o atributo `[Parameter]` para serem considerados parâmetros de componente.

O componente `Counter` a seguir define um parâmetro de componente chamado `IncrementAmount` que pode ser usado para especificar o valor que o `Counter` deve ser incrementado cada vez que o botão é clicado.

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

Para especificar um parâmetro de componente no mais bem, use um atributo como você faria em ASP.NET Web Forms:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Manipuladores de eventos

O ASP.NET Web Forms e o mais bem fornecem um modelo de programação baseado em eventos para manipular eventos de interface do usuário. Exemplos desses eventos incluem cliques de botão e entrada de texto. No ASP.NET Web Forms, você usa controles de servidor HTML para manipular eventos de interface do usuário expostos pelo DOM ou pode manipular eventos expostos por controles de servidor Web. Os eventos são exibidos no servidor por meio de solicitações de postback de formulário. Considere o seguinte Web Forms exemplo de clique de botão:

*Counter. ascx*

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

No mais alto, você pode registrar manipuladores para eventos da interface do usuário DOM diretamente usando atributos de diretiva do formulário `@on{event}`. O espaço reservado `{event}` representa o nome do evento. Por exemplo, você pode ouvir cliques de botão como este:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Os manipuladores de eventos podem aceitar um argumento opcional, específico do evento, para fornecer mais informações sobre o evento. Por exemplo, eventos de mouse podem usar um `MouseEventArgs` argumento, mas não é necessário.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Em vez de fazer referência a um grupo de métodos para um manipulador de eventos, você pode usar uma expressão lambda. Uma expressão lambda permite que você feche outros valores no escopo.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Os manipuladores de eventos podem ser executados de forma síncrona ou assíncrona. Por exemplo, o manipulador de eventos de `OnClick` a seguir é executado de forma assíncrona:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Depois que um evento é manipulado, o componente é renderizado para considerar qualquer alteração de estado de componente. Com manipuladores de eventos assíncronos, o componente é renderizado imediatamente após a execução do manipulador ser concluída. O componente é renderizado *novamente* após a conclusão da `Task` assíncrona. Esse modo de execução assíncrono fornece uma oportunidade de renderizar alguma interface do usuário apropriada enquanto o `Task` assíncrono ainda está em andamento.

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

Os componentes também podem definir seus próprios eventos definindo um parâmetro de componente do tipo `EventCallback<TValue>`. Os retornos de chamada de evento dão suporte a todas as variações de manipuladores de eventos de interface do usuário DOM: argumentos opcionais, síncronos ou assíncronos, grupos de métodos ou expressões lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Associação de dados

O mais fácil é um mecanismo simples para associar dados de um componente de interface do usuário ao estado do componente. Essa abordagem difere dos recursos do ASP.NET Web Forms para associação de dados de fontes de dados a controles de interface do usuário. Abordaremos o tratamento de dados de fontes de dados diferentes na seção [lidando com dados](data.md) .

Para criar uma associação de dados bidirecional de um componente de interface do usuário para o estado do componente, use o atributo de diretiva `@bind`. No exemplo a seguir, o valor da caixa de seleção é associado ao campo `isChecked`.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Quando o componente é renderizado, o valor da caixa de seleção é definido como o valor do campo `isChecked`. Quando o usuário alterna a caixa de seleção, o evento `onchange` é acionado e o campo `isChecked` é definido como o novo valor. O `@bind` sintaxe, nesse caso, é equivalente à seguinte marcação:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Para alterar o evento usado para a associação, use o atributo `@bind:event`.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Os componentes também podem dar suporte à ligação de dados com seus parâmetros. Para associação de dados, defina um parâmetro de retorno de chamada de evento com o mesmo nome que o parâmetro acoplável. O sufixo "alterado" é adicionado ao nome.

*PasswordBox. Razor*

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

Para encadear uma associação de dados a um elemento subjacente da interface do usuário, defina o valor e manipule o evento diretamente no elemento da interface do usuário em vez de usar o atributo `@bind`.

Para associar a um parâmetro de componente, use um atributo `@bind-{Parameter}` para especificar o parâmetro ao qual você deseja associar.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Alterações de estado

Se o estado do componente foi alterado fora de um evento de interface do usuário normal ou de retorno de chamada de evento, o componente deve sinalizar manualmente que ele precisa ser processado novamente. Para sinalizar que o estado de um componente foi alterado, chame o método `StateHasChanged` no componente.

No exemplo a seguir, um componente exibe uma mensagem de um serviço `AppState` que pode ser atualizado por outras partes do aplicativo. O componente registra seu método de `StateHasChanged` com o evento `AppState.OnChange` para que o componente seja renderizado sempre que a mensagem for atualizada.

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

## <a name="component-lifecycle"></a>Ciclo de vida do componente

O ASP.NET Web Forms Framework tem métodos de ciclo de vida bem definidos para módulos, páginas e controles. Por exemplo, o controle a seguir implementa manipuladores de eventos para os eventos de ciclo de vida `Init`, `Load`e `UnLoad`:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Os componentes mais fáceis também têm um ciclo de vida bem definido. O ciclo de vida de um componente pode ser usado para inicializar o estado do componente e implementar comportamentos avançados de componentes.

Todos os métodos de ciclo de vida de componentes de mais de um dos outros são síncronos e assíncronos. A renderização do componente é síncrona. Não é possível executar a lógica assíncrona como parte da renderização do componente. Toda a lógica assíncrona deve ser executada como parte de um método de ciclo de vida `async`.

### <a name="oninitialized"></a>OnInitialized

Os métodos `OnInitialized` e `OnInitializedAsync` são usados para inicializar o componente. Um componente é normalmente inicializado após sua primeira renderização. Depois que um componente é inicializado, ele pode ser renderizado várias vezes antes de ser Descartado. O método `OnInitialized` é semelhante ao evento `Page_Load` no ASP.NET Web Forms páginas e controles.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>Parameterset

Os métodos `OnParametersSet` e `OnParametersSetAsync` são chamados quando um componente recebe parâmetros de seu pai e o valor é atribuído a propriedades. Esses métodos são executados após a inicialização do componente e *cada vez que o componente é renderizado*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Os métodos `OnAfterRender` e `OnAfterRenderAsync` são chamados após a conclusão da renderização de um componente. Referências de elemento e componente são preenchidas neste ponto (mais sobre esses conceitos abaixo). A interatividade com o navegador está habilitada neste ponto. As interações com a execução do DOM e do JavaScript podem ocorrer com segurança.

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

`OnAfterRender` e `OnAfterRenderAsync` *não são chamados durante o pré-processamento no servidor*.

O parâmetro `firstRender` é `true` na primeira vez que o componente é renderizado; caso contrário, seu valor será `false`.

### <a name="idisposable"></a>IDisposable

Os componentes mais poseriais podem implementar `IDisposable` para descartar recursos quando o componente é removido da interface do usuário. Um componente Razor pode implementar `IDispose` usando a diretiva `@implements`:

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

## <a name="capture-component-references"></a>Capturar referências de componente

No ASP.NET Web Forms, é comum manipular uma instância de controle diretamente no código, referindo-se à sua ID. No mais grande, também é possível capturar e manipular uma referência a um componente, embora seja muito menos comum.

Para capturar uma referência de componente no mais incrivelmente, use o atributo de diretiva `@ref`. O valor do atributo deve corresponder ao nome de um campo configurável com o mesmo tipo do componente referenciado.

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

Quando o componente pai é renderizado, o campo é populado com a instância de componente filho. Em seguida, você pode chamar métodos em, ou então manipular, a instância do componente.

Não é recomendável manipular o estado do componente diretamente usando referências de componente. Isso impede que o componente seja renderizado automaticamente nos horários corretos.

## <a name="capture-element-references"></a>Capturar referências de elemento

Os componentes mais poseriais podem capturar referências a um elemento. Ao contrário dos controles de servidor HTML no ASP.NET Web Forms, você não pode manipular o DOM diretamente usando uma referência de elemento no mais incrivelmente. O mais incrivelmente lida com a maioria das interações de DOM para você usando seu algoritmo de comparação DOM. Referências de elemento capturado no mais incrivelmente são opacas. No entanto, eles são usados para passar uma referência de elemento específica em uma chamada de interoperabilidade JavaScript. Para obter mais informações sobre a interoperabilidade de JavaScript, consulte [ASP.NET Core a interoperabilidade de JavaScript mais incrivelmente](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Componentes de modelo

No ASP.NET Web Forms, você pode criar *controles modelo*. Controles de modelo permitem que o desenvolvedor especifique uma parte do HTML usada para renderizar um controle de contêiner. A mecânica da criação de controles de servidor modelo é complexa, mas permite cenários poderosos para a renderização de dados em uma maneira personalizável do usuário. Exemplos de controles de modelo incluem `Repeater` e `DataList`.

Os componentes mais poseriais também podem ser modelados definindo parâmetros de componente do tipo `RenderFragment` ou `RenderFragment<T>`. Um `RenderFragment` representa uma parte da marcação Razor que pode ser renderizada pelo componente. Uma `RenderFragment<T>` é uma parte da marcação Razor que usa um parâmetro que pode ser especificado quando o fragmento de renderização é renderizado.

### <a name="child-content"></a>Conteúdo filho

Os componentes mais bem podem capturar seu conteúdo filho como um `RenderFragment` e renderizar esse conteúdo como parte da renderização do componente. Para capturar o conteúdo filho, defina um parâmetro de componente do tipo `RenderFragment` e nomeie-o `ChildContent`.

*ChildContentComponent. Razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Um componente pai pode fornecer conteúdo filho usando sintaxe Razor normal.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Parâmetros de modelo

Um componente de mais de um modelo também pode definir vários parâmetros de componente do tipo `RenderFragment` ou `RenderFragment<T>`. O parâmetro para um `RenderFragment<T>` pode ser especificado quando é chamado. Para especificar um parâmetro de tipo genérico para um componente, use a diretiva `@typeparam` Razor.

*SimpleListView. Razor*

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

Ao usar um componente modelo, os parâmetros do modelo podem ser especificados usando elementos filho que correspondem aos nomes dos parâmetros. Os argumentos de componente do tipo `RenderFragment<T>` passados como elementos têm um parâmetro implícito denominado `context`. Você pode alterar o nome desse parâmetro de implementação usando o atributo `Context` no elemento filho. Qualquer parâmetro de tipo genérico pode ser especificado usando um atributo que corresponde ao nome do parâmetro de tipo. O parâmetro de tipo será inferido se possível:

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

A saída desse componente tem esta aparência:

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Code-behind

Um componente mais simples normalmente é criado em um único arquivo *. Razor* . No entanto, também é possível separar o código e a marcação usando um arquivo code-behind. Para usar um arquivo de componente, adicione C# um arquivo que corresponda ao nome do arquivo do componente, mas com uma extensão *. cs* adicionada (*Counter.Razor.cs*). Use o C# arquivo para definir uma classe base para o componente. Você pode nomear a classe base como desejar, mas é comum nomear a classe da mesma forma que a classe de componente, mas com uma extensão de `Base` adicionada (`CounterBase`). A classe baseada em componente também deve derivar de `ComponentBase`. Em seguida, no arquivo de componente Razor, adicione a diretiva `@inherits` para especificar a classe base para o componente (`@inherits CounterBase`).

*Counter. Razor*

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

A visibilidade dos membros do componente na classe base deve ser `protected` ou `public` ser visível para a classe de componente.

## <a name="additional-resources"></a>Recursos adicionais

O anterior não é um tratamento completo de todos os aspectos dos componentes mais completos. Para obter mais informações sobre como [criar e usar ASP.NET Core componentes do Razor](/aspnet/core/blazor/components), consulte a documentação mais bem.

>[!div class="step-by-step"]
>[Anterior](app-startup.md)
>[Próximo](pages-routing-layouts.md)
