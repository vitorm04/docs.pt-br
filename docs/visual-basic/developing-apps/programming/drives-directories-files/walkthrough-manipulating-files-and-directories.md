---
title: criar arquivos e diretórios
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333803"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="ce078-102">Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce078-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="ce078-103">Este passo a passo fornece uma introdução para os fundamentos de E/S de arquivo em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ce078-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="ce078-104">Ele descreve como criar um pequeno aplicativo que lista e examina os arquivos de texto em um diretório.</span><span class="sxs-lookup"><span data-stu-id="ce078-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="ce078-105">Para cada arquivo de texto selecionado, o aplicativo fornece atributos de arquivo e a primeira linha do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ce078-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="ce078-106">Há uma opção para gravar as informações em um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="ce078-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="ce078-107">Este passo a passo usa os membros do `My.Computer.FileSystem Object`, que estão disponíveis no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ce078-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="ce078-108">Consulte <xref:Microsoft.VisualBasic.FileIO.FileSystem> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ce078-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="ce078-109">No final do passo a passo, será fornecido um exemplo equivalente que usa classes do namespace <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="ce078-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="ce078-110">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="ce078-110">To create the project</span></span>  
  
1. <span data-ttu-id="ce078-111">No menu **Arquivo**, clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ce078-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="ce078-112">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="ce078-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="ce078-113">No painel **Modelos Instalados**, expanda **Visual Basic** e, em seguida, selecione **Windows**.</span><span class="sxs-lookup"><span data-stu-id="ce078-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="ce078-114">No meio do painel **Modelos**, clique em **Aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="ce078-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="ce078-115">Na caixa **Nome**, digite `FileExplorer` para definir o nome do projeto e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce078-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ce078-116">O Visual Studio adiciona o projeto ao **Gerenciador de Soluções** e o Designer de Formulários do Windows é exibido.</span><span class="sxs-lookup"><span data-stu-id="ce078-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="ce078-117">Adicione os controles da tabela a seguir no formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ce078-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="ce078-118">Controle</span><span class="sxs-lookup"><span data-stu-id="ce078-118">Control</span></span>|<span data-ttu-id="ce078-119">propriedade</span><span class="sxs-lookup"><span data-stu-id="ce078-119">Property</span></span>|<span data-ttu-id="ce078-120">Valor</span><span class="sxs-lookup"><span data-stu-id="ce078-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="ce078-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="ce078-121">**ListBox**</span></span>|<span data-ttu-id="ce078-122">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ce078-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="ce078-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="ce078-123">**Button**</span></span>|<span data-ttu-id="ce078-124">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ce078-124">**Name**</span></span><br /><br /> <span data-ttu-id="ce078-125">**Texto**</span><span class="sxs-lookup"><span data-stu-id="ce078-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="ce078-126">**Procurar**</span><span class="sxs-lookup"><span data-stu-id="ce078-126">**Browse**</span></span>|  
    |<span data-ttu-id="ce078-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="ce078-127">**Button**</span></span>|<span data-ttu-id="ce078-128">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ce078-128">**Name**</span></span><br /><br /> <span data-ttu-id="ce078-129">**Texto**</span><span class="sxs-lookup"><span data-stu-id="ce078-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="ce078-130">**Examinar**</span><span class="sxs-lookup"><span data-stu-id="ce078-130">**Examine**</span></span>|  
    |<span data-ttu-id="ce078-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="ce078-131">**CheckBox**</span></span>|<span data-ttu-id="ce078-132">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ce078-132">**Name**</span></span><br /><br /> <span data-ttu-id="ce078-133">**Texto**</span><span class="sxs-lookup"><span data-stu-id="ce078-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="ce078-134">**Salvar resultados**</span><span class="sxs-lookup"><span data-stu-id="ce078-134">**Save Results**</span></span>|  
    |<span data-ttu-id="ce078-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="ce078-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="ce078-136">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ce078-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="ce078-137">Para selecionar uma pasta e listar arquivos em uma pasta</span><span class="sxs-lookup"><span data-stu-id="ce078-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="ce078-138">Criar um manipulador de eventos `Click` para `browseButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="ce078-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="ce078-139">O Editor de Códigos é aberto.</span><span class="sxs-lookup"><span data-stu-id="ce078-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="ce078-140">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="ce078-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="ce078-141">A chamada `FolderBrowserDialog1.ShowDialog` abre a caixa de diálogo **Procurar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="ce078-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="ce078-142">Após o usuário clicar em **OK**, a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> será enviada como um argumento para o método `ListFiles`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="ce078-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="ce078-143">Adicione o seguinte método `ListFiles`.</span><span class="sxs-lookup"><span data-stu-id="ce078-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="ce078-144">Primeiro, esse código limpa a **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="ce078-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="ce078-145">Depois, o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> recupera uma coleção de cadeias de caracteres, uma para cada arquivo do diretório.</span><span class="sxs-lookup"><span data-stu-id="ce078-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="ce078-146">O método `GetFiles` aceita um argumento de padrão de pesquisa para recuperar os arquivos que correspondem a um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="ce078-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="ce078-147">Neste exemplo, somente os arquivos que têm a extensão .txt serão retornados.</span><span class="sxs-lookup"><span data-stu-id="ce078-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="ce078-148">As cadeias de caracteres retornadas pelo método `GetFiles` serão adicionadas à **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="ce078-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="ce078-149">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-149">Run the application.</span></span> <span data-ttu-id="ce078-150">Clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="ce078-150">Click the **Browse** button.</span></span> <span data-ttu-id="ce078-151">Na caixa de diálogo **Procurar Pasta**, navegue até uma pasta que contenha os arquivos .txt e, em seguida, selecione a pasta e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce078-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="ce078-152">A `ListBox` contém uma lista de arquivos .txt na pasta selecionada.</span><span class="sxs-lookup"><span data-stu-id="ce078-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="ce078-153">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="ce078-154">Para obter atributos de um arquivo e o conteúdo de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="ce078-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="ce078-155">Criar um manipulador de eventos `Click` para `examineButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="ce078-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="ce078-156">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="ce078-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="ce078-157">O código verifica se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ce078-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="ce078-158">Então, ele obtém a entrada de caminho do arquivo da `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ce078-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="ce078-159">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> é usado para verificar se o arquivo ainda existe.</span><span class="sxs-lookup"><span data-stu-id="ce078-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="ce078-160">O caminho do arquivo será enviado como um argumento para o método `GetTextForOutput`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="ce078-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="ce078-161">Esse método retorna uma cadeia de caracteres que contém informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ce078-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="ce078-162">As informações do arquivo aparecem em uma **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="ce078-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="ce078-163">Adicione o seguinte método `GetTextForOutput`.</span><span class="sxs-lookup"><span data-stu-id="ce078-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="ce078-164">O código usa o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> para obter parâmetros do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ce078-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="ce078-165">Os parâmetros do arquivo são adicionados a um <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="ce078-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="ce078-166">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lê o conteúdo do arquivo em um <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="ce078-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="ce078-167">A primeira linha do conteúdo é obtida de `StreamReader` e é adicionada no `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="ce078-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="ce078-168">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-168">Run the application.</span></span> <span data-ttu-id="ce078-169">Clique em **Procurar** e navegue até uma pasta que contenha os arquivos .txt.</span><span class="sxs-lookup"><span data-stu-id="ce078-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="ce078-170">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce078-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="ce078-171">Selecione um arquivo na `ListBox` e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="ce078-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="ce078-172">Uma `MessageBox` mostra as informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ce078-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="ce078-173">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="ce078-174">Para adicionar uma entrada de log</span><span class="sxs-lookup"><span data-stu-id="ce078-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="ce078-175">Adicione o seguinte código ao final do manipulador de eventos de `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ce078-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="ce078-176">O código define o caminho do arquivo de log, a fim de colocar o arquivo de log no mesmo diretório que o arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="ce078-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="ce078-177">O texto da entrada de log é definido com a data e hora atuais, seguido pelas informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ce078-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="ce078-178">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, com o argumento `append` definido como `True`, é usado para criar a entrada de log.</span><span class="sxs-lookup"><span data-stu-id="ce078-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="ce078-179">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-179">Run the application.</span></span> <span data-ttu-id="ce078-180">Navegue até um arquivo de texto, selecione-o na `ListBox`, escolha a caixa de seleção **Salvar Resultados** e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="ce078-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="ce078-181">Verifique se a entrada de log foi gravada para o arquivo `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="ce078-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="ce078-182">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="ce078-183">Para usar o diretório atual</span><span class="sxs-lookup"><span data-stu-id="ce078-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="ce078-184">Crie um manipulador de eventos para `Form1_Load`, clicando duas vezes no formulário.</span><span class="sxs-lookup"><span data-stu-id="ce078-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="ce078-185">Adicione o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ce078-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="ce078-186">Esse código define o diretório padrão do navegador de pastas para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ce078-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="ce078-187">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-187">Run the application.</span></span> <span data-ttu-id="ce078-188">Quando você clica em **Procurar** pela primeira vez, a caixa de diálogo **Procurar Pasta** é aberta no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ce078-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="ce078-189">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="ce078-190">Para habilitar controles de maneira seletiva</span><span class="sxs-lookup"><span data-stu-id="ce078-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="ce078-191">Adicione o seguinte método `SetEnabled`.</span><span class="sxs-lookup"><span data-stu-id="ce078-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="ce078-192">O método `SetEnabled` habilita ou desabilita os controles, dependendo se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ce078-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="ce078-193">Criar um manipulador de eventos `SelectedIndexChanged` para `filesListBox`, clicando duas vezes no controle `ListBox` no formulário.</span><span class="sxs-lookup"><span data-stu-id="ce078-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="ce078-194">Adicione uma chamada para `SetEnabled` no novo manipulador de eventos `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="ce078-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="ce078-195">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ce078-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="ce078-196">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="ce078-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="ce078-197">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce078-197">Run the application.</span></span> <span data-ttu-id="ce078-198">A caixa de seleção **Salvar Resultados** e o botão **Examinar** ficarão desabilitados se um item não for selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ce078-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="ce078-199">Exemplo completo usando My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="ce078-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="ce078-200">A seguir está o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="ce078-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="ce078-201">Exemplo completo usando System.IO</span><span class="sxs-lookup"><span data-stu-id="ce078-201">Full example using System.IO</span></span>  

 <span data-ttu-id="ce078-202">O exemplo equivalente a seguir usa classes do namespace <xref:System.IO> em vez de usar objetos `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="ce078-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="ce078-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce078-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="ce078-204">Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce078-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
