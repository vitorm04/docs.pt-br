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
ms.openlocfilehash: ab1c119d2c5cd9bfa0ff725774144bc65817cad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592503"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="c254c-102">Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c254c-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="c254c-103">Este passo a passo fornece uma introdução para os fundamentos de E/S de arquivo em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c254c-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="c254c-104">Ele descreve como criar um pequeno aplicativo que lista e examina os arquivos de texto em um diretório.</span><span class="sxs-lookup"><span data-stu-id="c254c-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="c254c-105">Para cada arquivo de texto selecionado, o aplicativo fornece atributos de arquivo e a primeira linha do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c254c-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="c254c-106">Há uma opção para gravar as informações em um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="c254c-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="c254c-107">Este passo a passo usa os membros do `My.Computer.FileSystem Object`, que estão disponíveis no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c254c-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="c254c-108">Consulte <xref:Microsoft.VisualBasic.FileIO.FileSystem> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c254c-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="c254c-109">No final do passo a passo, será fornecido um exemplo equivalente que usa classes do namespace <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="c254c-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="c254c-110">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="c254c-110">To create the project</span></span>  
  
1.  <span data-ttu-id="c254c-111">No menu **Arquivo**, clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="c254c-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="c254c-112">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="c254c-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="c254c-113">No painel **Modelos Instalados**, expanda **Visual Basic** e, em seguida, selecione **Windows**.</span><span class="sxs-lookup"><span data-stu-id="c254c-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="c254c-114">No meio do painel **Modelos**, clique em **Aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="c254c-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="c254c-115">Na caixa **Nome**, digite `FileExplorer` para definir o nome do projeto e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c254c-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c254c-116">O Visual Studio adiciona o projeto ao **Gerenciador de Soluções** e o Designer de Formulários do Windows é exibido.</span><span class="sxs-lookup"><span data-stu-id="c254c-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="c254c-117">Adicione os controles da tabela a seguir no formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="c254c-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="c254c-118">Controle</span><span class="sxs-lookup"><span data-stu-id="c254c-118">Control</span></span>|<span data-ttu-id="c254c-119">propriedade</span><span class="sxs-lookup"><span data-stu-id="c254c-119">Property</span></span>|<span data-ttu-id="c254c-120">Valor</span><span class="sxs-lookup"><span data-stu-id="c254c-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="c254c-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="c254c-121">**ListBox**</span></span>|<span data-ttu-id="c254c-122">**Nome**</span><span class="sxs-lookup"><span data-stu-id="c254c-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="c254c-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="c254c-123">**Button**</span></span>|<span data-ttu-id="c254c-124">**Nome**</span><span class="sxs-lookup"><span data-stu-id="c254c-124">**Name**</span></span><br /><br /> <span data-ttu-id="c254c-125">**Texto**</span><span class="sxs-lookup"><span data-stu-id="c254c-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="c254c-126">**Procurar**</span><span class="sxs-lookup"><span data-stu-id="c254c-126">**Browse**</span></span>|  
    |<span data-ttu-id="c254c-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="c254c-127">**Button**</span></span>|<span data-ttu-id="c254c-128">**Nome**</span><span class="sxs-lookup"><span data-stu-id="c254c-128">**Name**</span></span><br /><br /> <span data-ttu-id="c254c-129">**Texto**</span><span class="sxs-lookup"><span data-stu-id="c254c-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="c254c-130">**Examinar**</span><span class="sxs-lookup"><span data-stu-id="c254c-130">**Examine**</span></span>|  
    |<span data-ttu-id="c254c-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="c254c-131">**CheckBox**</span></span>|<span data-ttu-id="c254c-132">**Nome**</span><span class="sxs-lookup"><span data-stu-id="c254c-132">**Name**</span></span><br /><br /> <span data-ttu-id="c254c-133">**Texto**</span><span class="sxs-lookup"><span data-stu-id="c254c-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="c254c-134">**Salvar resultados**</span><span class="sxs-lookup"><span data-stu-id="c254c-134">**Save Results**</span></span>|  
    |<span data-ttu-id="c254c-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="c254c-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="c254c-136">**Nome**</span><span class="sxs-lookup"><span data-stu-id="c254c-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="c254c-137">Para selecionar uma pasta e listar arquivos em uma pasta</span><span class="sxs-lookup"><span data-stu-id="c254c-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="c254c-138">Criar um manipulador de eventos `Click` para `browseButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="c254c-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="c254c-139">O Editor de Códigos é aberto.</span><span class="sxs-lookup"><span data-stu-id="c254c-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="c254c-140">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="c254c-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     <span data-ttu-id="c254c-141">A chamada `FolderBrowserDialog1.ShowDialog` abre a caixa de diálogo **Procurar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="c254c-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="c254c-142">Após o usuário clicar em **OK**, a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> será enviada como um argumento para o método `ListFiles`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="c254c-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="c254c-143">Adicione o seguinte método `ListFiles`.</span><span class="sxs-lookup"><span data-stu-id="c254c-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     <span data-ttu-id="c254c-144">Primeiro, esse código limpa a **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="c254c-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="c254c-145">Depois, o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> recupera uma coleção de cadeias de caracteres, uma para cada arquivo do diretório.</span><span class="sxs-lookup"><span data-stu-id="c254c-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="c254c-146">O método `GetFiles` aceita um argumento de padrão de pesquisa para recuperar os arquivos que correspondem a um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="c254c-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="c254c-147">Neste exemplo, somente os arquivos que têm a extensão .txt serão retornados.</span><span class="sxs-lookup"><span data-stu-id="c254c-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="c254c-148">As cadeias de caracteres retornadas pelo método `GetFiles` serão adicionadas à **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="c254c-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="c254c-149">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-149">Run the application.</span></span> <span data-ttu-id="c254c-150">Clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="c254c-150">Click the **Browse** button.</span></span> <span data-ttu-id="c254c-151">Na caixa de diálogo **Procurar Pasta**, navegue até uma pasta que contenha os arquivos .txt e, em seguida, selecione a pasta e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c254c-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="c254c-152">A `ListBox` contém uma lista de arquivos .txt na pasta selecionada.</span><span class="sxs-lookup"><span data-stu-id="c254c-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="c254c-153">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="c254c-154">Para obter atributos de um arquivo e o conteúdo de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="c254c-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="c254c-155">Criar um manipulador de eventos `Click` para `examineButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="c254c-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="c254c-156">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="c254c-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     <span data-ttu-id="c254c-157">O código verifica se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c254c-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="c254c-158">Então, ele obtém a entrada de caminho do arquivo da `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c254c-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="c254c-159">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> é usado para verificar se o arquivo ainda existe.</span><span class="sxs-lookup"><span data-stu-id="c254c-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="c254c-160">O caminho do arquivo será enviado como um argumento para o método `GetTextForOutput`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="c254c-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="c254c-161">Esse método retorna uma cadeia de caracteres que contém informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c254c-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="c254c-162">As informações do arquivo aparecem em uma **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="c254c-162">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="c254c-163">Adicione o seguinte método `GetTextForOutput`.</span><span class="sxs-lookup"><span data-stu-id="c254c-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     <span data-ttu-id="c254c-164">O código usa o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> para obter parâmetros do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c254c-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="c254c-165">Os parâmetros do arquivo são adicionados a um <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c254c-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="c254c-166">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lê o conteúdo do arquivo em um <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="c254c-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="c254c-167">A primeira linha do conteúdo é obtida de `StreamReader` e é adicionada no `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="c254c-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="c254c-168">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-168">Run the application.</span></span> <span data-ttu-id="c254c-169">Clique em **Procurar** e navegue até uma pasta que contenha os arquivos .txt.</span><span class="sxs-lookup"><span data-stu-id="c254c-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="c254c-170">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c254c-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="c254c-171">Selecione um arquivo na `ListBox` e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="c254c-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="c254c-172">Uma `MessageBox` mostra as informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c254c-172">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="c254c-173">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="c254c-174">Para adicionar uma entrada de log</span><span class="sxs-lookup"><span data-stu-id="c254c-174">To add a log entry</span></span>  
  
1.  <span data-ttu-id="c254c-175">Adicione o seguinte código ao final do manipulador de eventos de `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="c254c-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     <span data-ttu-id="c254c-176">O código define o caminho do arquivo de log, a fim de colocar o arquivo de log no mesmo diretório que o arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="c254c-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="c254c-177">O texto da entrada de log é definido com a data e hora atuais, seguido pelas informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c254c-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="c254c-178">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, com o argumento `append` definido como `True`, é usado para criar a entrada de log.</span><span class="sxs-lookup"><span data-stu-id="c254c-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="c254c-179">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-179">Run the application.</span></span> <span data-ttu-id="c254c-180">Navegue até um arquivo de texto, selecione-o na `ListBox`, escolha a caixa de seleção **Salvar Resultados** e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="c254c-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="c254c-181">Verifique se a entrada de log foi gravada para o arquivo `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="c254c-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="c254c-182">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="c254c-183">Para usar o diretório atual</span><span class="sxs-lookup"><span data-stu-id="c254c-183">To use the current directory</span></span>  
  
1.  <span data-ttu-id="c254c-184">Crie um manipulador de eventos para `Form1_Load`, clicando duas vezes no formulário.</span><span class="sxs-lookup"><span data-stu-id="c254c-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="c254c-185">Adicione o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c254c-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     <span data-ttu-id="c254c-186">Esse código define o diretório padrão do navegador de pastas para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c254c-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="c254c-187">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-187">Run the application.</span></span> <span data-ttu-id="c254c-188">Quando você clica em **Procurar** pela primeira vez, a caixa de diálogo **Procurar Pasta** é aberta no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c254c-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="c254c-189">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="c254c-190">Para habilitar controles de maneira seletiva</span><span class="sxs-lookup"><span data-stu-id="c254c-190">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="c254c-191">Adicione o seguinte método `SetEnabled`.</span><span class="sxs-lookup"><span data-stu-id="c254c-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     <span data-ttu-id="c254c-192">O método `SetEnabled` habilita ou desabilita os controles, dependendo se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c254c-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="c254c-193">Criar um manipulador de eventos `SelectedIndexChanged` para `filesListBox`, clicando duas vezes no controle `ListBox` no formulário.</span><span class="sxs-lookup"><span data-stu-id="c254c-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="c254c-194">Adicione uma chamada para `SetEnabled` no novo manipulador de eventos `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="c254c-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="c254c-195">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="c254c-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="c254c-196">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="c254c-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="c254c-197">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c254c-197">Run the application.</span></span> <span data-ttu-id="c254c-198">A caixa de seleção **Salvar Resultados** e o botão **Examinar** ficarão desabilitados se um item não for selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c254c-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="c254c-199">Exemplo completo usando My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c254c-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="c254c-200">A seguir está o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="c254c-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="c254c-201">Exemplo completo usando System.IO</span><span class="sxs-lookup"><span data-stu-id="c254c-201">Full example using System.IO</span></span>  
 <span data-ttu-id="c254c-202">O exemplo equivalente a seguir usa classes do namespace <xref:System.IO> em vez de usar objetos `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="c254c-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c254c-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c254c-203">See Also</span></span>  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [<span data-ttu-id="c254c-204">Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c254c-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
