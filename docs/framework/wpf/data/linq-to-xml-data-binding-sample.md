---
title: Exemplo de associação de dados LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920933"
---
# <a name="linq-to-xml-data-binding-sample"></a><span data-ttu-id="609ad-102">Exemplo de associação de dados LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="609ad-102">LINQ to XML data binding sample</span></span>

<span data-ttu-id="609ad-103">Este artigo descreve o exemplo LinqToXmlDataBinding, um aplicativo Windows Presentation Foundation (WPF) que associa os componentes da interface do usuário a uma fonte de dados XML inserida.</span><span class="sxs-lookup"><span data-stu-id="609ad-103">This article describes the LinqToXmlDataBinding sample, a Windows Presentation Foundation (WPF) app that binds user interface components to an embedded XML data source.</span></span>

## <a name="overview"></a><span data-ttu-id="609ad-104">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="609ad-104">Overview</span></span>

<span data-ttu-id="609ad-105">O exemplo LinqToXmlDataBinding é um aplicativo Windows Presentation Foundation (WPF) que contém C# e arquivos de origem XAML.</span><span class="sxs-lookup"><span data-stu-id="609ad-105">The LinqToXmlDataBinding sample is a Windows Presentation Foundation (WPF) app that contains C# and XAML source files.</span></span> <span data-ttu-id="609ad-106">Um documento XML inserido define uma lista de livros.</span><span class="sxs-lookup"><span data-stu-id="609ad-106">An embedded XML document defines a list of books.</span></span> <span data-ttu-id="609ad-107">O aplicativo permite que o usuário exiba, adicione, exclua e edite as entradas do livro.</span><span class="sxs-lookup"><span data-stu-id="609ad-107">The app enables the user to view, add, delete, and edit the book entries.</span></span>

<span data-ttu-id="609ad-108">Há dois arquivos de origem principais:</span><span class="sxs-lookup"><span data-stu-id="609ad-108">There are two primary source files:</span></span>

- <span data-ttu-id="609ad-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contém o código de declaração XAML para a interface do usuário da janela principal.</span><span class="sxs-lookup"><span data-stu-id="609ad-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contains the XAML declaration code for the user interface (UI) of the main window.</span></span> <span data-ttu-id="609ad-110">Ele também contém uma seção de recursos de janela que define um provedor de dados e um documento XML inserido para as listagens de livros.</span><span class="sxs-lookup"><span data-stu-id="609ad-110">It also contains a window resource section that defines a data provider and an embedded XML document for the book listings.</span></span>

- <span data-ttu-id="609ad-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contém os métodos de inicialização e de manipulação de eventos associados à interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="609ad-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contains the initialization and event-handling methods associated with the UI.</span></span>

<span data-ttu-id="609ad-112">A janela principal é dividida nas quatro seções verticais de interface de usuário:</span><span class="sxs-lookup"><span data-stu-id="609ad-112">The main window is divided into the following four vertical UI sections:</span></span>

- <span data-ttu-id="609ad-113">**XML** exibe o código-fonte XML bruto da listagem de livros inserida.</span><span class="sxs-lookup"><span data-stu-id="609ad-113">**XML** displays the raw XML source of the embedded book listing.</span></span>

- <span data-ttu-id="609ad-114">**Lista de livros** exibe as entradas de livro como texto padrão e permite que o usuário selecione e exclua entradas individuais.</span><span class="sxs-lookup"><span data-stu-id="609ad-114">**Book List** displays the book entries as standard text and enables the user to select and delete individual entries.</span></span>

- <span data-ttu-id="609ad-115">**Editar Livro Selecionado** permite que o usuário edite os valores associados à entrada do livro selecionada no momento.</span><span class="sxs-lookup"><span data-stu-id="609ad-115">**Edit Selected Book** enables the user to edit the values associated with the currently selected book entry.</span></span>

- <span data-ttu-id="609ad-116">**Adicionar Novo Livro** habilita a criação de uma nova entrada de livro com base nos valores inseridos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="609ad-116">**Add New Book** enables the creation of a new book entry based on values entered by the user.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="609ad-117">Executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="609ad-117">Run the sample</span></span>

<span data-ttu-id="609ad-118">Esta seção mostra como criar e compilar o projeto LinqToXmlDataBinding no Visual Studio e como executar o aplicativo LinqToXmlDataBinding Windows Presentation Foundation (WPF) resultante.</span><span class="sxs-lookup"><span data-stu-id="609ad-118">This section shows how to create and build the LinqToXmlDataBinding project in Visual Studio, and how to run the resulting LinqToXmlDataBinding Windows Presentation Foundation (WPF) app.</span></span>

### <a name="create-the-project"></a><span data-ttu-id="609ad-119">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="609ad-119">Create the project</span></span>

1. <span data-ttu-id="609ad-120">Inicie o Visual Studio e crie um **WPF App** em C# chamado **LinqToXmlDataBinding**.</span><span class="sxs-lookup"><span data-stu-id="609ad-120">Open Visual Studio and create a C# **WPF App** named **LinqToXmlDataBinding**.</span></span>

   <span data-ttu-id="609ad-121">O projeto deve direcionar o .NET Framework 3.5 (ou posterior).</span><span class="sxs-lookup"><span data-stu-id="609ad-121">The project should target the .NET Framework 3.5 (or later).</span></span>

1. <span data-ttu-id="609ad-122">Se ainda não presentes, adicione referências de projeto para os seguintes conjuntos de módulos (assemblies) .NET:</span><span class="sxs-lookup"><span data-stu-id="609ad-122">If not already present, add project references for the following .NET assemblies:</span></span>

    - <span data-ttu-id="609ad-123">System.Data</span><span class="sxs-lookup"><span data-stu-id="609ad-123">System.Data</span></span>
    - <span data-ttu-id="609ad-124">System.Data.DataSetExtensions</span><span class="sxs-lookup"><span data-stu-id="609ad-124">System.Data.DataSetExtensions</span></span>
    - <span data-ttu-id="609ad-125">System.Xml</span><span class="sxs-lookup"><span data-stu-id="609ad-125">System.Xml</span></span>
    - <span data-ttu-id="609ad-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="609ad-126">System.Xml</span></span>

1. <span data-ttu-id="609ad-127">Crie a solução pressionando **Ctrl**+**Shift**+**B** e execute-a pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="609ad-127">Build the solution by pressing **Ctrl**+**Shift**+**B**, then run it by pressing **F5**.</span></span>

   <span data-ttu-id="609ad-128">O projeto deve compilar sem erros e como executar um aplicativo genérica de WPF.</span><span class="sxs-lookup"><span data-stu-id="609ad-128">The project should compile without errors and run as a generic WPF application.</span></span>

### <a name="add-code"></a><span data-ttu-id="609ad-129">Adicionar código</span><span class="sxs-lookup"><span data-stu-id="609ad-129">Add code</span></span>

1. <span data-ttu-id="609ad-130">No **Gerenciador de Soluções**, renomeie o arquivo de origem **Window1.xaml** como **L2XDBForm.xaml**.</span><span class="sxs-lookup"><span data-stu-id="609ad-130">In **Solution Explorer**, rename the source file **Window1.xaml** to **L2XDBForm.xaml**.</span></span>

   <span data-ttu-id="609ad-131">O arquivo de origem dependente Window1.xaml.cs é automaticamente renomeado para L2XDBForm.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="609ad-131">The dependent source file Window1.xaml.cs is automatically renamed to L2XDBForm.xaml.cs.</span></span>

1. <span data-ttu-id="609ad-132">Substitua o código-fonte encontrado no arquivo **L2XDBForm. XAML** pelo [código-fonte L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="609ad-132">Replace the source code found in the file **L2XDBForm.xaml** with the [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="609ad-133">Use o modo de exibição XAML para trabalhar com esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="609ad-133">Use the XAML source view to work with this file.</span></span>

1. <span data-ttu-id="609ad-134">Da mesma forma, substitua a origem em **L2XDBForm.XAML.cs** pelo [código-fonte L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="609ad-134">Similarly, replace the source in **L2XDBForm.xaml.cs** with the [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

1. <span data-ttu-id="609ad-135">No arquivo **app. XAML**, substitua todas as ocorrências da cadeia de caracteres **Window1. XAML** por **L2XDBForm. XAML**.</span><span class="sxs-lookup"><span data-stu-id="609ad-135">In the file **App.xaml**, replace all occurrences of the string **Window1.xaml** with **L2XDBForm.xaml**.</span></span>

1. <span data-ttu-id="609ad-136">Crie a solução pressionando **Ctrl**+**Shift**+**B**.</span><span class="sxs-lookup"><span data-stu-id="609ad-136">Build the solution by pressing **Ctrl**+**Shift**+**B**.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="609ad-137">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="609ad-137">Run the app</span></span>

<span data-ttu-id="609ad-138">O aplicativo LinqToXmlDataBinding permite que o usuário exiba e manipule uma lista de livros que é armazenada como um elemento XML inserido.</span><span class="sxs-lookup"><span data-stu-id="609ad-138">The LinqToXmlDataBinding app enables the user to view and manipulate a list of books that's stored as an embedded XML element.</span></span> <span data-ttu-id="609ad-139">Execute o aplicativo pressionando **F5** (Iniciar Depuração) ou **Ctrl**+**F5** (Iniciar sem depuração).</span><span class="sxs-lookup"><span data-stu-id="609ad-139">Run the app by pressing **F5** (Start Debugging) or **Ctrl**+**F5** (Start Without Debugging).</span></span>

<span data-ttu-id="609ad-140">É exibida uma janela de programa com o título **Associação de dados do WPF usando LINQ to XML**.</span><span class="sxs-lookup"><span data-stu-id="609ad-140">A program window with the title **WPF Data Binding using LINQ to XML** appears.</span></span>

<span data-ttu-id="609ad-141">A seção superior da interface do usuário exibe o **XML** bruto que representa a lista de livros.</span><span class="sxs-lookup"><span data-stu-id="609ad-141">The top section of the UI displays the raw **XML** that represents the book list.</span></span> <span data-ttu-id="609ad-142">É exibida usando um controle de <xref:System.Windows.Controls.TextBlock> WPF, que não permite a interação por meio do mouse ou do teclado.</span><span class="sxs-lookup"><span data-stu-id="609ad-142">It is displayed using a WPF <xref:System.Windows.Controls.TextBlock> control, which does not enable interaction through the mouse or keyboard.</span></span>

<span data-ttu-id="609ad-143">A segunda seção vertical, rotulada como **Lista de livros**, exibe os livros como uma lista ordenada de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="609ad-143">The second vertical section, labeled **Book List**, displays the books as a plain text ordered list.</span></span> <span data-ttu-id="609ad-144">Usa um controle de <xref:System.Windows.Controls.ListBox> que permite a seleção embora o mouse ou o teclado.</span><span class="sxs-lookup"><span data-stu-id="609ad-144">It uses a <xref:System.Windows.Controls.ListBox> control that enables selection though the mouse or keyboard.</span></span>

### <a name="add-and-delete-books"></a><span data-ttu-id="609ad-145">Adicionar e excluir livros</span><span class="sxs-lookup"><span data-stu-id="609ad-145">Add and delete books</span></span>

<span data-ttu-id="609ad-146">Para adicionar um novo livro à lista, insira valores na **ID** e no **valor** <xref:System.Windows.Controls.TextBox> controles na última seção, **Adicionar novo livro**e, em seguida, selecione **Adicionar livro**.</span><span class="sxs-lookup"><span data-stu-id="609ad-146">To add a new book to the list, enter values into the **ID** and **Value** <xref:System.Windows.Controls.TextBox> controls in the last section, **Add New Book**, and then select **Add Book**.</span></span> <span data-ttu-id="609ad-147">O livro é acrescentado à lista no livro e nas listagens XML.</span><span class="sxs-lookup"><span data-stu-id="609ad-147">The book is appended to the list in both the book and XML listings.</span></span> <span data-ttu-id="609ad-148">Este programa não validar valores de entrada.</span><span class="sxs-lookup"><span data-stu-id="609ad-148">This program does not validate input values.</span></span>

<span data-ttu-id="609ad-149">Para excluir um livro existente da lista, selecione-o na seção **lista de livros** e, em seguida, selecione **remover livro selecionado**.</span><span class="sxs-lookup"><span data-stu-id="609ad-149">To delete an existing book from the list, select it in the **Book List** section, and then select **Remove Selected Book**.</span></span> <span data-ttu-id="609ad-150">A entrada do livro é removida do livro e das listagens de origem XML brutas.</span><span class="sxs-lookup"><span data-stu-id="609ad-150">The book entry is removed from both the book and the raw XML source listings.</span></span>

### <a name="edit-a-book-entry"></a><span data-ttu-id="609ad-151">Editar uma entrada de livro</span><span class="sxs-lookup"><span data-stu-id="609ad-151">Edit a book entry</span></span>

1. <span data-ttu-id="609ad-152">Selecione a entrada de livro na segunda seção da **Lista de livros**.</span><span class="sxs-lookup"><span data-stu-id="609ad-152">Select the book entry in the second **Book List** section.</span></span>

   <span data-ttu-id="609ad-153">Seus valores atuais são exibidos na seção **Editar livro selecionado** .</span><span class="sxs-lookup"><span data-stu-id="609ad-153">Its current values are displayed in the **Edit Selected Book** section.</span></span>

1. <span data-ttu-id="609ad-154">Editar os valores usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="609ad-154">Edit the values using the keyboard.</span></span> <span data-ttu-id="609ad-155">Assim que o controle de <xref:System.Windows.Controls.TextBox> perde o foco, as alterações são automaticamente propagadas para a origem XML e listagens de livros.</span><span class="sxs-lookup"><span data-stu-id="609ad-155">As soon as either <xref:System.Windows.Controls.TextBox> control loses focus, changes are automatically propagated to the XML source and book listings.</span></span>
