---
title: Manipulando arquivos e diretórios no Visual Basic
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
ms.openlocfilehash: cb7fda617118c01e6ee54339bcc3ff8f8b342450
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202438"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="e1cb0-102">Passo a passo: Manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1cb0-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="e1cb0-103">Este passo a passo fornece uma introdução para os fundamentos de E/S de arquivo em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="e1cb0-104">Ele descreve como criar um pequeno aplicativo que lista e examina os arquivos de texto em um diretório.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="e1cb0-105">Para cada arquivo de texto selecionado, o aplicativo fornece atributos de arquivo e a primeira linha do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="e1cb0-106">Há uma opção para gravar as informações em um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="e1cb0-107">Este passo a passo usa os membros do `My.Computer.FileSystem Object`, que estão disponíveis no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="e1cb0-108">Consulte <xref:Microsoft.VisualBasic.FileIO.FileSystem> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="e1cb0-109">No final do passo a passo, será fornecido um exemplo equivalente que usa classes do namespace <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="e1cb0-110">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="e1cb0-110">To create the project</span></span>  
  
1.  <span data-ttu-id="e1cb0-111">No menu **Arquivo**, clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="e1cb0-112">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="e1cb0-113">No painel **Modelos Instalados**, expanda **Visual Basic** e, em seguida, selecione **Windows**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="e1cb0-114">No meio do painel **Modelos**, clique em **Aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e1cb0-115">Na caixa **Nome**, digite `FileExplorer` para definir o nome do projeto e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e1cb0-116">O Visual Studio adiciona o projeto ao **Gerenciador de Soluções** e o Designer de Formulários do Windows é exibido.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="e1cb0-117">Adicione os controles da tabela a seguir no formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="e1cb0-118">Controle</span><span class="sxs-lookup"><span data-stu-id="e1cb0-118">Control</span></span>|<span data-ttu-id="e1cb0-119">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e1cb0-119">Property</span></span>|<span data-ttu-id="e1cb0-120">Valor</span><span class="sxs-lookup"><span data-stu-id="e1cb0-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="e1cb0-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-121">**ListBox**</span></span>|<span data-ttu-id="e1cb0-122">**Nome**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="e1cb0-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-123">**Button**</span></span>|<span data-ttu-id="e1cb0-124">**Nome**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-124">**Name**</span></span><br /><br /> <span data-ttu-id="e1cb0-125">**Texto**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="e1cb0-126">**Procurar**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-126">**Browse**</span></span>|  
    |<span data-ttu-id="e1cb0-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-127">**Button**</span></span>|<span data-ttu-id="e1cb0-128">**Nome**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-128">**Name**</span></span><br /><br /> <span data-ttu-id="e1cb0-129">**Texto**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="e1cb0-130">**Examinar**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-130">**Examine**</span></span>|  
    |<span data-ttu-id="e1cb0-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-131">**CheckBox**</span></span>|<span data-ttu-id="e1cb0-132">**Nome**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-132">**Name**</span></span><br /><br /> <span data-ttu-id="e1cb0-133">**Texto**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="e1cb0-134">**Salvar resultados**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-134">**Save Results**</span></span>|  
    |<span data-ttu-id="e1cb0-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="e1cb0-136">**Nome**</span><span class="sxs-lookup"><span data-stu-id="e1cb0-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="e1cb0-137">Para selecionar uma pasta e listar arquivos em uma pasta</span><span class="sxs-lookup"><span data-stu-id="e1cb0-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="e1cb0-138">Criar um manipulador de eventos `Click` para `browseButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="e1cb0-139">O Editor de Códigos é aberto.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="e1cb0-140">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="e1cb0-141">A chamada `FolderBrowserDialog1.ShowDialog` abre a caixa de diálogo **Procurar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="e1cb0-142">Após o usuário clicar em **OK**, a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> será enviada como um argumento para o método `ListFiles`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="e1cb0-143">Adicione o seguinte método `ListFiles`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="e1cb0-144">Primeiro, esse código limpa a **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="e1cb0-145">Depois, o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> recupera uma coleção de cadeias de caracteres, uma para cada arquivo do diretório.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="e1cb0-146">O método `GetFiles` aceita um argumento de padrão de pesquisa para recuperar os arquivos que correspondem a um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="e1cb0-147">Neste exemplo, somente os arquivos que têm a extensão .txt serão retornados.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="e1cb0-148">As cadeias de caracteres retornadas pelo método `GetFiles` serão adicionadas à **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="e1cb0-149">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-149">Run the application.</span></span> <span data-ttu-id="e1cb0-150">Clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-150">Click the **Browse** button.</span></span> <span data-ttu-id="e1cb0-151">Na caixa de diálogo **Procurar Pasta**, navegue até uma pasta que contenha os arquivos .txt e, em seguida, selecione a pasta e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="e1cb0-152">A `ListBox` contém uma lista de arquivos .txt na pasta selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="e1cb0-153">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="e1cb0-154">Para obter atributos de um arquivo e o conteúdo de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="e1cb0-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="e1cb0-155">Criar um manipulador de eventos `Click` para `examineButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="e1cb0-156">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="e1cb0-157">O código verifica se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="e1cb0-158">Então, ele obtém a entrada de caminho do arquivo da `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="e1cb0-159">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> é usado para verificar se o arquivo ainda existe.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="e1cb0-160">O caminho do arquivo será enviado como um argumento para o método `GetTextForOutput`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="e1cb0-161">Esse método retorna uma cadeia de caracteres que contém informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="e1cb0-162">As informações do arquivo aparecem em uma **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-162">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="e1cb0-163">Adicione o seguinte método `GetTextForOutput`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="e1cb0-164">O código usa o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> para obter parâmetros do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="e1cb0-165">Os parâmetros do arquivo são adicionados a um <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="e1cb0-166">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lê o conteúdo do arquivo em um <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="e1cb0-167">A primeira linha do conteúdo é obtida de `StreamReader` e é adicionada no `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="e1cb0-168">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-168">Run the application.</span></span> <span data-ttu-id="e1cb0-169">Clique em **Procurar** e navegue até uma pasta que contenha os arquivos .txt.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="e1cb0-170">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="e1cb0-171">Selecione um arquivo na `ListBox` e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="e1cb0-172">Uma `MessageBox` mostra as informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-172">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="e1cb0-173">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="e1cb0-174">Para adicionar uma entrada de log</span><span class="sxs-lookup"><span data-stu-id="e1cb0-174">To add a log entry</span></span>  
  
1.  <span data-ttu-id="e1cb0-175">Adicione o seguinte código ao final do manipulador de eventos de `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="e1cb0-176">O código define o caminho do arquivo de log, a fim de colocar o arquivo de log no mesmo diretório que o arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="e1cb0-177">O texto da entrada de log é definido com a data e hora atuais, seguido pelas informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="e1cb0-178">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, com o argumento `append` definido como `True`, é usado para criar a entrada de log.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="e1cb0-179">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-179">Run the application.</span></span> <span data-ttu-id="e1cb0-180">Navegue até um arquivo de texto, selecione-o na `ListBox`, escolha a caixa de seleção **Salvar Resultados** e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="e1cb0-181">Verifique se a entrada de log foi gravada para o arquivo `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="e1cb0-182">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="e1cb0-183">Para usar o diretório atual</span><span class="sxs-lookup"><span data-stu-id="e1cb0-183">To use the current directory</span></span>  
  
1.  <span data-ttu-id="e1cb0-184">Crie um manipulador de eventos para `Form1_Load`, clicando duas vezes no formulário.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="e1cb0-185">Adicione o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="e1cb0-186">Esse código define o diretório padrão do navegador de pastas para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="e1cb0-187">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-187">Run the application.</span></span> <span data-ttu-id="e1cb0-188">Quando você clica em **Procurar** pela primeira vez, a caixa de diálogo **Procurar Pasta** é aberta no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="e1cb0-189">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="e1cb0-190">Para habilitar controles de maneira seletiva</span><span class="sxs-lookup"><span data-stu-id="e1cb0-190">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="e1cb0-191">Adicione o seguinte método `SetEnabled`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="e1cb0-192">O método `SetEnabled` habilita ou desabilita os controles, dependendo se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="e1cb0-193">Criar um manipulador de eventos `SelectedIndexChanged` para `filesListBox`, clicando duas vezes no controle `ListBox` no formulário.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="e1cb0-194">Adicione uma chamada para `SetEnabled` no novo manipulador de eventos `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="e1cb0-195">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="e1cb0-196">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="e1cb0-197">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-197">Run the application.</span></span> <span data-ttu-id="e1cb0-198">A caixa de seleção **Salvar Resultados** e o botão **Examinar** ficarão desabilitados se um item não for selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="e1cb0-199">Exemplo completo usando My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="e1cb0-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="e1cb0-200">A seguir está o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="e1cb0-201">Exemplo completo usando System.IO</span><span class="sxs-lookup"><span data-stu-id="e1cb0-201">Full example using System.IO</span></span>  
 <span data-ttu-id="e1cb0-202">O exemplo equivalente a seguir usa classes do namespace <xref:System.IO> em vez de usar objetos `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="e1cb0-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1cb0-203">See also</span></span>
- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="e1cb0-204">Passo a passo: Manipulando arquivos usando métodos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e1cb0-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
