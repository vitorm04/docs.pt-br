---
title: Código-fonte de L2DBForm.xaml
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 290b00e136f0c49e1b27d4fa1bca7321eebe936e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920940"
---
# <a name="l2dbformxaml-source-code"></a><span data-ttu-id="df8d4-102">Código-fonte de L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="df8d4-102">L2DBForm.xaml source code</span></span>

<span data-ttu-id="df8d4-103">Esta página contém e descreve o arquivo de origem XAML para a [ligação de dados do WPF usando LINQ to XML exemplo](linq-to-xml-data-binding-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df8d4-103">This page contains and describes the XAML source file for the [WPF data binding using LINQ to XML example](linq-to-xml-data-binding-sample.md).</span></span>

## <a name="overall-ui-structure"></a><span data-ttu-id="df8d4-104">Estrutura geral da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="df8d4-104">Overall UI structure</span></span>

<span data-ttu-id="df8d4-105">Como é comum para um projeto do WPF, esse arquivo contém um elemento pai, um <xref:System.Windows.Window> elemento XML associado à classe derivada `L2XDBFrom` no namespace `LinqToXmlDataBinding`.</span><span class="sxs-lookup"><span data-stu-id="df8d4-105">As is typical for a WPF project, this file contains one parent element, a <xref:System.Windows.Window> XML element that's associated with the derived class `L2XDBFrom` in the `LinqToXmlDataBinding` namespace.</span></span>

<span data-ttu-id="df8d4-106">A área do cliente está contida em um <xref:System.Windows.Controls.StackPanel> que recebe um plano de fundo azul claro.</span><span class="sxs-lookup"><span data-stu-id="df8d4-106">The client area is contained within a <xref:System.Windows.Controls.StackPanel> that's given a light blue background.</span></span> <span data-ttu-id="df8d4-107">Esse painel contém quatro seções de <xref:System.Windows.Controls.DockPanel> interface do usuário separados por barras de <xref:System.Windows.Controls.Separator> .</span><span class="sxs-lookup"><span data-stu-id="df8d4-107">This panel contains four <xref:System.Windows.Controls.DockPanel> UI sections separated by <xref:System.Windows.Controls.Separator> bars.</span></span> <span data-ttu-id="df8d4-108">A finalidade dessas seções é descrita [aqui](linq-to-xml-data-binding-sample.md#overview).</span><span class="sxs-lookup"><span data-stu-id="df8d4-108">The purpose of these sections is described [here](linq-to-xml-data-binding-sample.md#overview).</span></span>

<span data-ttu-id="df8d4-109">Cada seção contém um rótulo que a identifica.</span><span class="sxs-lookup"><span data-stu-id="df8d4-109">Each section contains a label that identifies it.</span></span> <span data-ttu-id="df8d4-110">Nas duas primeiras seções, este rótulo é girada em 90 graus com o uso de <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="df8d4-110">In the first two sections, this label is rotated 90 degrees through the use of a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span></span> <span data-ttu-id="df8d4-111">O restante da seção contém elementos de interface do usuário apropriados para a finalidade dessa seção, por exemplo, blocos de texto, caixas de texto e botões.</span><span class="sxs-lookup"><span data-stu-id="df8d4-111">The rest of the section contains UI elements appropriate to the purpose of that section, for example, text blocks, text boxes, and buttons.</span></span> <span data-ttu-id="df8d4-112">Um filho <xref:System.Windows.Controls.StackPanel> são às vezes para alinhar esses controles filho.</span><span class="sxs-lookup"><span data-stu-id="df8d4-112">Sometimes a child <xref:System.Windows.Controls.StackPanel> is used to align these child controls.</span></span>

## <a name="window-resource-section"></a><span data-ttu-id="df8d4-113">Seção de recursos de janela</span><span class="sxs-lookup"><span data-stu-id="df8d4-113">Window resource section</span></span>

<span data-ttu-id="df8d4-114">A marca de abertura `<Window.Resources>` na linha 9 indica o início da seção de recursos da janela.</span><span class="sxs-lookup"><span data-stu-id="df8d4-114">The opening `<Window.Resources>` tag on line 9 indicates the start of the window resource section.</span></span> <span data-ttu-id="df8d4-115">Termina com a marca de fechamento na linha 35.</span><span class="sxs-lookup"><span data-stu-id="df8d4-115">It ends with the closing tag on line 35.</span></span>

<span data-ttu-id="df8d4-116">A marca de `<ObjectDataProvider>` , que abrange as linhas 11 a 25, declara <xref:System.Windows.Data.ObjectDataProvider>, `LoadedBooks`chamado, que usa <xref:System.Xml.Linq.XElement> como a fonte.</span><span class="sxs-lookup"><span data-stu-id="df8d4-116">The `<ObjectDataProvider>` tag, which spans lines 11 through 25, declares a <xref:System.Windows.Data.ObjectDataProvider>, named `LoadedBooks`, that uses an <xref:System.Xml.Linq.XElement> as the source.</span></span> <span data-ttu-id="df8d4-117">O <xref:System.Xml.Linq.XElement> é inicializado analisando um documento XML inserido (um elemento `CDATA`).</span><span class="sxs-lookup"><span data-stu-id="df8d4-117">The <xref:System.Xml.Linq.XElement> is initialized by parsing an embedded XML document (a `CDATA` element).</span></span> <span data-ttu-id="df8d4-118">Observe que o espaço em branco é preservado ao declarar o documento XML inserido e também quando ele é analisado.</span><span class="sxs-lookup"><span data-stu-id="df8d4-118">Notice that white space is preserved when declaring the embedded XML document and also when it's parsed.</span></span> <span data-ttu-id="df8d4-119">O espaço em branco é preservado porque o controle <xref:System.Windows.Controls.TextBlock>, que é usado para exibir o XML, não tem funcionalidades especiais de formatação de XML.</span><span class="sxs-lookup"><span data-stu-id="df8d4-119">White space is preserved because the <xref:System.Windows.Controls.TextBlock> control, which is used to display the raw XML, has no special XML formatting capabilities.</span></span>

<span data-ttu-id="df8d4-120">Finalmente, <xref:System.Windows.DataTemplate> chamado `BookTemplate` é definido em linhas 28 a 34.</span><span class="sxs-lookup"><span data-stu-id="df8d4-120">Lastly, a <xref:System.Windows.DataTemplate> named `BookTemplate` is defined on lines 28 through 34.</span></span> <span data-ttu-id="df8d4-121">Este modelo é usado para exibir as entradas na seção de interface do usuário da **Lista de Livros**.</span><span class="sxs-lookup"><span data-stu-id="df8d4-121">This template is used to display the entries in the **Book List** UI section.</span></span> <span data-ttu-id="df8d4-122">Usa associação de dados e propriedades dinâmicas LINQ to XML para recuperar a identificação do livro e o nome de livro com as atribuições seguintes:</span><span class="sxs-lookup"><span data-stu-id="df8d4-122">It uses data binding and LINQ to XML dynamic properties to retrieve the book ID and book name through the following assignments:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a><span data-ttu-id="df8d4-123">Código de associação de dados</span><span class="sxs-lookup"><span data-stu-id="df8d4-123">Data binding code</span></span>

<span data-ttu-id="df8d4-124">Além do elemento de <xref:System.Windows.DataTemplate> , associação de dados é usada em um número de outros locais neste arquivo.</span><span class="sxs-lookup"><span data-stu-id="df8d4-124">In addition to the <xref:System.Windows.DataTemplate> element, data binding is used in a number of other places in this file.</span></span>

<span data-ttu-id="df8d4-125">Na marca de abertura `<StackPanel>` na linha 38, a propriedade de <xref:System.Windows.FrameworkElement.DataContext%2A> desse painel é definida para o provedor de dados de `LoadedBooks` .</span><span class="sxs-lookup"><span data-stu-id="df8d4-125">In the opening `<StackPanel>` tag on line 38, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of this panel is set to the `LoadedBooks` data provider.</span></span>

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

<span data-ttu-id="df8d4-126">Definir o contexto de dados possibilita (na linha 46) que o <xref:System.Windows.Controls.TextBlock> chamado `tbRawXml` exiba o XML bruto associando-se à propriedade `Xml` deste provedor de dados:</span><span class="sxs-lookup"><span data-stu-id="df8d4-126">Setting the data context makes it possible (on line 46) for the <xref:System.Windows.Controls.TextBlock> named `tbRawXml` to display the raw XML by binding to this data provider's `Xml` property:</span></span>

```xaml
Text="{Binding Path=Xml}"
```

<span data-ttu-id="df8d4-127">A <xref:System.Windows.Controls.ListBox> na seção da interface do usuário **Lista de Livros**, nas linhas 58 a 62, define o modelo para seus itens de exibição como o `BookTemplate` definido na seção de recursos de janela:</span><span class="sxs-lookup"><span data-stu-id="df8d4-127">The <xref:System.Windows.Controls.ListBox> in the **Book List** UI section, on lines 58 through 62, sets the template for its display items to the `BookTemplate` defined in the window resource section:</span></span>

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

<span data-ttu-id="df8d4-128">Em seguida, linhas 59 a 62, os valores reais dos livros são associados à caixa de listagem:</span><span class="sxs-lookup"><span data-stu-id="df8d4-128">Then, on lines 59 through 62, the actual values of the books are bound to this list box:</span></span>

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

<span data-ttu-id="df8d4-129">A terceira seção da interface do usuário, **Editar Livro Selecionado**, primeiro associa o <xref:System.Windows.FrameworkElement.DataContext%2A> do <xref:System.Windows.Controls.StackPanel> pai ao item que está selecionado no momento na seção da interface do usuário **Lista de Livros** (linha 82):</span><span class="sxs-lookup"><span data-stu-id="df8d4-129">The third UI section, **Edit Selected Book**, first binds the <xref:System.Windows.FrameworkElement.DataContext%2A> of the parent <xref:System.Windows.Controls.StackPanel> to the currently selected item in from the **Book List** UI section (line 82):</span></span>

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

<span data-ttu-id="df8d4-130">Ele usa a associação de dados bidirecional para que os valores atuais dos elementos de livro sejam exibidos e atualizados das duas caixas de texto nesse painel.</span><span class="sxs-lookup"><span data-stu-id="df8d4-130">It then uses two-way data binding, so that the current values of the book elements are displayed to, and updated from, the two text boxes in this panel.</span></span> <span data-ttu-id="df8d4-131">A associação de dados a propriedades dinâmicas é semelhante àquela usada no modelo de dados `BookTemplate`:</span><span class="sxs-lookup"><span data-stu-id="df8d4-131">Data binding to dynamic properties is similar to the data binding used in the `BookTemplate` data template:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

<span data-ttu-id="df8d4-132">A última seção da interface do usuário, **Adicionar Novo Livro**, não usa associação de dados em seu código XAML.</span><span class="sxs-lookup"><span data-stu-id="df8d4-132">The last UI section, **Add New Book**, doesn't use data binding in its XAML code.</span></span> <span data-ttu-id="df8d4-133">Em vez disso, a associação de dados está no código de manipulação de eventos no arquivo *L2DBForm.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="df8d4-133">Instead, data binding is in its event handling code in the file *L2DBForm.xaml.cs*.</span></span>

## <a name="example"></a><span data-ttu-id="df8d4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df8d4-134">Example</span></span>

### <a name="description"></a><span data-ttu-id="df8d4-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="df8d4-135">Description</span></span>

> [!NOTE]
> <span data-ttu-id="df8d4-136">Recomendamos que você copie o seguinte código abaixo em um editor de códigos, como o editor de código-fonte C# no Visual Studio, de modo que a linha números é mais fácil de controlar.</span><span class="sxs-lookup"><span data-stu-id="df8d4-136">We recommend that you copy the following code below into a code editor, such as the C# source code editor in Visual Studio, so that line numbers will be easier to track.</span></span>

### <a name="code"></a><span data-ttu-id="df8d4-137">Código</span><span class="sxs-lookup"><span data-stu-id="df8d4-137">Code</span></span>

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a><span data-ttu-id="df8d4-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="df8d4-138">Comments</span></span>

<span data-ttu-id="df8d4-139">Para obter o código-fonte C# dos manipuladores de eventos associados aos elementos de interface do usuário do WPF, confira [Código-fonte de L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="df8d4-139">For the C# source code for the event handlers associated with the WPF UI elements, see [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df8d4-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df8d4-140">See also</span></span>

- [<span data-ttu-id="df8d4-141">Passo a passo: exemplo de LinqToXmlDataBinding</span><span class="sxs-lookup"><span data-stu-id="df8d4-141">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="df8d4-142">Código-fonte de L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="df8d4-142">L2DBForm.xaml.cs source code</span></span>](l2dbform-xaml-cs-source-code.md)
