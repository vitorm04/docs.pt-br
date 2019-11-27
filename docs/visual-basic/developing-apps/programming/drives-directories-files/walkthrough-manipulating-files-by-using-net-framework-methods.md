---
title: manipular arquivos usando métodos do .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333779"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="b1512-102">Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1512-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="b1512-103">Estas instruções passo a passo demonstram como abrir e ler um arquivo usando a classe <xref:System.IO.StreamReader>, verificar se um arquivo está sendo acessado, pesquisar uma cadeia de caracteres dentro de um arquivo lido com uma instância da classe <xref:System.IO.StreamReader> e gravar em um arquivo usando a classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="b1512-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="b1512-104">Criando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b1512-104">Creating the Application</span></span>

<span data-ttu-id="b1512-105">Inicie o Visual Studio e comece o projeto criando um formulário que o usuário pode usar para gravar no arquivo designado.</span><span class="sxs-lookup"><span data-stu-id="b1512-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="b1512-106">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="b1512-106">To create the project</span></span>

1. <span data-ttu-id="b1512-107">No menu **Arquivo**, selecione **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="b1512-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="b1512-108">No painel **Novo Projeto**, clique em **Aplicativos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="b1512-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="b1512-109">Na caixa **Nome**, digite `MyDiary` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1512-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="b1512-110">O Visual Studio adiciona o projeto ao **Gerenciador de Soluções** e o **Designer de Formulários do Windows** é aberto.</span><span class="sxs-lookup"><span data-stu-id="b1512-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="b1512-111">Adicione os controles na tabela a seguir ao formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b1512-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="b1512-112">**Object**</span><span class="sxs-lookup"><span data-stu-id="b1512-112">**Object**</span></span>|<span data-ttu-id="b1512-113">**Propriedades**</span><span class="sxs-lookup"><span data-stu-id="b1512-113">**Properties**</span></span>|<span data-ttu-id="b1512-114">**Value**</span><span class="sxs-lookup"><span data-stu-id="b1512-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-115">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-115">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-116">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="b1512-117">**Enviar entrada**</span><span class="sxs-lookup"><span data-stu-id="b1512-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-118">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-118">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-119">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="b1512-120">**Limpar entrada**</span><span class="sxs-lookup"><span data-stu-id="b1512-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="b1512-121">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-121">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-122">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-122">**Text**</span></span><br /><br /> <span data-ttu-id="b1512-123">**Multilinha**</span><span class="sxs-lookup"><span data-stu-id="b1512-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="b1512-124">**Digite algo.**</span><span class="sxs-lookup"><span data-stu-id="b1512-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="b1512-125">Gravando no arquivo</span><span class="sxs-lookup"><span data-stu-id="b1512-125">Writing to the File</span></span>

<span data-ttu-id="b1512-126">Para adicionar a capacidade de gravar em um arquivo por meio do aplicativo, use a classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="b1512-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="b1512-127"><xref:System.IO.StreamWriter> foi criado para a saída de caracteres em uma determinada codificação, enquanto a classe <xref:System.IO.Stream> foi criada para entrada e saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="b1512-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="b1512-128">Use <xref:System.IO.StreamWriter> para gravar linhas de informações em um arquivo de texto padrão.</span><span class="sxs-lookup"><span data-stu-id="b1512-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="b1512-129">Para saber mais sobre a classe <xref:System.IO.StreamWriter>, veja <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="b1512-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="b1512-130">Para adicionar a funcionalidade de gravação</span><span class="sxs-lookup"><span data-stu-id="b1512-130">To add writing functionality</span></span>

1. <span data-ttu-id="b1512-131">No menu **Exibição**, escolha **Código** para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="b1512-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="b1512-132">Como o aplicativo faz referência ao namespace <xref:System.IO>, adicione as seguintes instruções ao início do seu código, antes da declaração de classe para o formulário, que inicia `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="b1512-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="b1512-133">Antes de gravar no arquivo, você precisa criar uma instância de uma classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="b1512-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="b1512-134">No menu **Exibição**, escolha **Designer** para voltar para o **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="b1512-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="b1512-135">Clique duas vezes no botão `Submit` para criar um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b1512-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="b1512-136">O IDE (ambiente de desenvolvimento integrado) do Visual Studio retornará ao Editor de código e posicionará o ponto de inserção dentro do manipulador de eventos, no qual você deve adicionar o código.</span><span class="sxs-lookup"><span data-stu-id="b1512-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="b1512-137">Para gravar o arquivo, use o método <xref:System.IO.StreamWriter.Write%2A> da classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="b1512-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="b1512-138">Adicione o código a seguir diretamente após `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="b1512-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="b1512-139">Você não precisa se preocupar se uma exceção será gerada caso o arquivo não seja encontrado, porque ele será criado se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="b1512-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="b1512-140">Certifique-se de que o usuário não possa enviar uma entrada em branco adicionando o código a seguir diretamente após `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="b1512-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="b1512-141">Como este é uma diário, o usuário desejará atribuir uma data a cada entrada.</span><span class="sxs-lookup"><span data-stu-id="b1512-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="b1512-142">Insira o código a seguir após `fw = New StreamWriter("C:\MyDiary.txt", True)` para definir a variável `Today` como a data atual.</span><span class="sxs-lookup"><span data-stu-id="b1512-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="b1512-143">Por fim, anexe o código para limpar a <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b1512-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="b1512-144">Adicione o seguinte código ao evento `Clear` do botão <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="b1512-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="b1512-145">Adicionando recursos de exibição ao diário</span><span class="sxs-lookup"><span data-stu-id="b1512-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="b1512-146">Nesta seção, você adiciona um recurso que exibe a última entrada em `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b1512-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="b1512-147">Você também pode adicionar uma <xref:System.Windows.Forms.ComboBox> que exiba várias entradas e a partir da qual um usuário pode selecionar uma entrada para exibir o `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b1512-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="b1512-148">Uma instância da classe <xref:System.IO.StreamReader> é lida de `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="b1512-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="b1512-149">Como a classe <xref:System.IO.StreamWriter>, o <xref:System.IO.StreamReader> deve ser usado com arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="b1512-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="b1512-150">Para esta seção do passo a passo, adicione os controles na tabela a seguir ao formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b1512-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="b1512-151">Controle</span><span class="sxs-lookup"><span data-stu-id="b1512-151">Control</span></span>|<span data-ttu-id="b1512-152">{1&gt;Propriedades&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b1512-152">Properties</span></span>|<span data-ttu-id="b1512-153">Valores</span><span class="sxs-lookup"><span data-stu-id="b1512-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="b1512-154">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-154">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-155">**Visível**</span><span class="sxs-lookup"><span data-stu-id="b1512-155">**Visible**</span></span><br /><br /> <span data-ttu-id="b1512-156">**Size**</span><span class="sxs-lookup"><span data-stu-id="b1512-156">**Size**</span></span><br /><br /> <span data-ttu-id="b1512-157">**Multilinha**</span><span class="sxs-lookup"><span data-stu-id="b1512-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-158">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-158">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-159">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="b1512-160">**Vídeo**</span><span class="sxs-lookup"><span data-stu-id="b1512-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-161">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-161">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-162">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="b1512-163">**Obter entradas**</span><span class="sxs-lookup"><span data-stu-id="b1512-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="b1512-164">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-164">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-165">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-165">**Text**</span></span><br /><br /> <span data-ttu-id="b1512-166">**Habilitado**</span><span class="sxs-lookup"><span data-stu-id="b1512-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="b1512-167">**Selecionar uma entrada**</span><span class="sxs-lookup"><span data-stu-id="b1512-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="b1512-168">Para popular a caixa de combinação</span><span class="sxs-lookup"><span data-stu-id="b1512-168">To populate the combo box</span></span>

1. <span data-ttu-id="b1512-169">A `PickEntries`<xref:System.Windows.Forms.ComboBox> é usada para exibir as datas em que um usuário envia cada entrada, para que o usuário possa selecionar uma entrada de uma data específica.</span><span class="sxs-lookup"><span data-stu-id="b1512-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="b1512-170">Crie um identificador de evento <xref:System.Windows.Forms.Control.Click> para o botão `GetEntries` e adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="b1512-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="b1512-171">Para testar seu código, pressione F5 para compilar o aplicativo e, então, clique em **Obter entradas**.</span><span class="sxs-lookup"><span data-stu-id="b1512-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="b1512-172">Clique na seta do menu suspenso no <xref:System.Windows.Forms.ComboBox> para exibir as datas de entrada.</span><span class="sxs-lookup"><span data-stu-id="b1512-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="b1512-173">Para escolher e exibir entradas individuais</span><span class="sxs-lookup"><span data-stu-id="b1512-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="b1512-174">Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `Display` e adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="b1512-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="b1512-175">Para testar seu código, pressione F5 para compilar o aplicativo e, então, envie uma entrada.</span><span class="sxs-lookup"><span data-stu-id="b1512-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="b1512-176">Clique em **Obter Entradas**, selecione uma entrada da <xref:System.Windows.Forms.ComboBox> e clique em **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="b1512-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="b1512-177">Os conteúdos da entrada selecionada são exibidos no `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b1512-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="b1512-178">Habilitando usuários a excluir ou modificar entradas</span><span class="sxs-lookup"><span data-stu-id="b1512-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="b1512-179">Por fim, você pode incluir uma funcionalidade adicional que permite que os usuários excluam ou modifiquem uma entrada usando os botões `DeleteEntry` e `EditEntry`.</span><span class="sxs-lookup"><span data-stu-id="b1512-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="b1512-180">Os dois botões permanecem desabilitados a menos que uma entrada seja exibida.</span><span class="sxs-lookup"><span data-stu-id="b1512-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="b1512-181">Adicione os controles na tabela a seguir ao formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b1512-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="b1512-182">Controle</span><span class="sxs-lookup"><span data-stu-id="b1512-182">Control</span></span>|<span data-ttu-id="b1512-183">{1&gt;Propriedades&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b1512-183">Properties</span></span>|<span data-ttu-id="b1512-184">Valores</span><span class="sxs-lookup"><span data-stu-id="b1512-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-185">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-185">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-186">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-186">**Text**</span></span><br /><br /> <span data-ttu-id="b1512-187">**Habilitado**</span><span class="sxs-lookup"><span data-stu-id="b1512-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="b1512-188">**Excluir entrada**</span><span class="sxs-lookup"><span data-stu-id="b1512-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-189">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-189">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-190">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-190">**Text**</span></span><br /><br /> <span data-ttu-id="b1512-191">**Habilitado**</span><span class="sxs-lookup"><span data-stu-id="b1512-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="b1512-192">**Editar entrada**</span><span class="sxs-lookup"><span data-stu-id="b1512-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="b1512-193">**Nome**</span><span class="sxs-lookup"><span data-stu-id="b1512-193">**Name**</span></span><br /><br /> <span data-ttu-id="b1512-194">**Texto**</span><span class="sxs-lookup"><span data-stu-id="b1512-194">**Text**</span></span><br /><br /> <span data-ttu-id="b1512-195">**Habilitado**</span><span class="sxs-lookup"><span data-stu-id="b1512-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="b1512-196">**Enviar edição**</span><span class="sxs-lookup"><span data-stu-id="b1512-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="b1512-197">Para habilitar a exclusão e modificação de entradas</span><span class="sxs-lookup"><span data-stu-id="b1512-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="b1512-198">Adicione o seguinte código ao evento `Display` do botão <xref:System.Windows.Forms.Control.Click> , depois de `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="b1512-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="b1512-199">Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `DeleteEntry` e adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="b1512-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="b1512-200">Quando um usuário exibe uma entrada, o botão `EditEntry` fica habilitado.</span><span class="sxs-lookup"><span data-stu-id="b1512-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="b1512-201">Adicione o seguinte código ao evento <xref:System.Windows.Forms.Control.Click> do botão `Display`, depois de `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="b1512-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="b1512-202">Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `EditEntry` e adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="b1512-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="b1512-203">Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `SubmitEdit` e adicione o seguinte código</span><span class="sxs-lookup"><span data-stu-id="b1512-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="b1512-204">Para testar seu código, pressione F5 para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1512-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="b1512-205">Clique em **Obter Entradas**, selecione uma entrada e clique em **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="b1512-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="b1512-206">A entrada aparece na `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b1512-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="b1512-207">Clique em **Editar entrada**.</span><span class="sxs-lookup"><span data-stu-id="b1512-207">Click **Edit Entry**.</span></span> <span data-ttu-id="b1512-208">A entrada aparece na `Entry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b1512-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="b1512-209">Edite a entrada na `Entry`<xref:System.Windows.Forms.TextBox> e clique em **Enviar Edição**.</span><span class="sxs-lookup"><span data-stu-id="b1512-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="b1512-210">Abra o arquivo `MyDiary.txt` para confirmar a correção.</span><span class="sxs-lookup"><span data-stu-id="b1512-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="b1512-211">Agora, selecione uma entrada e clique em **Excluir entrada**.</span><span class="sxs-lookup"><span data-stu-id="b1512-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="b1512-212">Quando o <xref:System.Windows.Forms.MessageBox> solicita confirmação, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1512-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="b1512-213">Feche o aplicativo e abra `MyDiary.txt` para confirmar a exclusão.</span><span class="sxs-lookup"><span data-stu-id="b1512-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1512-214">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1512-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="b1512-215">Explicações Passo a Passo</span><span class="sxs-lookup"><span data-stu-id="b1512-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
