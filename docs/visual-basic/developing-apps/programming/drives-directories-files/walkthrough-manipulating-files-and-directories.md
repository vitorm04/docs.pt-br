---
title: "Manipulando arquivos e diretórios no Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- files, reading text
- reading files, text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files, walkthroughs
- Visual Basic code, file access
- files, writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files, walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e66d062df07fc23dfbd5d509e08ccd08813db15
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="9d653-102">Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d653-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="9d653-103">Este passo a passo fornece uma introdução aos fundamentos de E/S de arquivo no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d653-103">This walkthrough provides an introduction to the fundamentals of file I/O in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="9d653-104">Ele descreve como criar um pequeno aplicativo que lista e examina os arquivos de texto em um diretório.</span><span class="sxs-lookup"><span data-stu-id="9d653-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="9d653-105">Para cada arquivo de texto selecionado, o aplicativo fornece atributos de arquivo e a primeira linha do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9d653-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="9d653-106">Há uma opção para gravar as informações em um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="9d653-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="9d653-107">Este passo a passo usa os membros de `My.Computer.FileSystem Object`, que estão disponível em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d653-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="9d653-108">Consulte <xref:Microsoft.VisualBasic.FileIO.FileSystem> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9d653-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="9d653-109">No final do passo a passo, será fornecido um exemplo equivalente que usa classes do namespace <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="9d653-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="9d653-110">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="9d653-110">To create the project</span></span>  
  
1.  <span data-ttu-id="9d653-111">No menu **Arquivo**, clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="9d653-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="9d653-112">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="9d653-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="9d653-113">No painel **Modelos Instalados**, expanda **Visual Basic** e, em seguida, selecione **Windows**.</span><span class="sxs-lookup"><span data-stu-id="9d653-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="9d653-114">No meio do painel **Modelos**, clique em **Aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="9d653-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="9d653-115">Na caixa **Nome**, digite `FileExplorer` para definir o nome do projeto e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d653-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9d653-116">O [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adiciona o projeto ao **Gerenciador de Soluções** e o Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="9d653-116">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="9d653-117">Adicione os controles da tabela a seguir no formulário e defina os valores correspondentes para as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="9d653-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="9d653-118">Controle</span><span class="sxs-lookup"><span data-stu-id="9d653-118">Control</span></span>|<span data-ttu-id="9d653-119">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9d653-119">Property</span></span>|<span data-ttu-id="9d653-120">Valor</span><span class="sxs-lookup"><span data-stu-id="9d653-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="9d653-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="9d653-121">**ListBox**</span></span>|<span data-ttu-id="9d653-122">**Nome**</span><span class="sxs-lookup"><span data-stu-id="9d653-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="9d653-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="9d653-123">**Button**</span></span>|<span data-ttu-id="9d653-124">**Nome**</span><span class="sxs-lookup"><span data-stu-id="9d653-124">**Name**</span></span><br /><br /> <span data-ttu-id="9d653-125">**Texto**</span><span class="sxs-lookup"><span data-stu-id="9d653-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="9d653-126">**Procurar**</span><span class="sxs-lookup"><span data-stu-id="9d653-126">**Browse**</span></span>|  
    |<span data-ttu-id="9d653-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="9d653-127">**Button**</span></span>|<span data-ttu-id="9d653-128">**Nome**</span><span class="sxs-lookup"><span data-stu-id="9d653-128">**Name**</span></span><br /><br /> <span data-ttu-id="9d653-129">**Texto**</span><span class="sxs-lookup"><span data-stu-id="9d653-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="9d653-130">**Examinar**</span><span class="sxs-lookup"><span data-stu-id="9d653-130">**Examine**</span></span>|  
    |<span data-ttu-id="9d653-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="9d653-131">**CheckBox**</span></span>|<span data-ttu-id="9d653-132">**Nome**</span><span class="sxs-lookup"><span data-stu-id="9d653-132">**Name**</span></span><br /><br /> <span data-ttu-id="9d653-133">**Texto**</span><span class="sxs-lookup"><span data-stu-id="9d653-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="9d653-134">**Salvar resultados**</span><span class="sxs-lookup"><span data-stu-id="9d653-134">**Save Results**</span></span>|  
    |<span data-ttu-id="9d653-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="9d653-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="9d653-136">**Nome**</span><span class="sxs-lookup"><span data-stu-id="9d653-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="9d653-137">Para selecionar uma pasta e listar arquivos em uma pasta</span><span class="sxs-lookup"><span data-stu-id="9d653-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="9d653-138">Criar um manipulador de eventos `Click` para `browseButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="9d653-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="9d653-139">O Editor de Códigos é aberto.</span><span class="sxs-lookup"><span data-stu-id="9d653-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="9d653-140">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="9d653-140">Add the following code to the `Click` event handler.</span></span>  
  
     <span data-ttu-id="9d653-141">[!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-141">[!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]</span></span>  
  
     <span data-ttu-id="9d653-142">A chamada `FolderBrowserDialog1.ShowDialog` abre a caixa de diálogo **Procurar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="9d653-142">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="9d653-143">Após o usuário clicar em **OK**, a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> será enviada como um argumento para o método `ListFiles`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="9d653-143">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="9d653-144">Adicione o seguinte método `ListFiles`.</span><span class="sxs-lookup"><span data-stu-id="9d653-144">Add the following `ListFiles` method.</span></span>  
  
     <span data-ttu-id="9d653-145">[!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-145">[!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]</span></span>  
  
     <span data-ttu-id="9d653-146">Primeiro, esse código limpa a **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="9d653-146">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="9d653-147">Depois, o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> recupera uma coleção de cadeias de caracteres, uma para cada arquivo do diretório.</span><span class="sxs-lookup"><span data-stu-id="9d653-147">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="9d653-148">O método `GetFiles` aceita um argumento de padrão de pesquisa para recuperar os arquivos que correspondem a um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="9d653-148">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="9d653-149">Neste exemplo, somente os arquivos que têm a extensão .txt serão retornados.</span><span class="sxs-lookup"><span data-stu-id="9d653-149">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="9d653-150">As cadeias de caracteres retornadas pelo método `GetFiles` serão adicionadas à **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="9d653-150">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="9d653-151">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-151">Run the application.</span></span> <span data-ttu-id="9d653-152">Clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="9d653-152">Click the **Browse** button.</span></span> <span data-ttu-id="9d653-153">Na caixa de diálogo **Procurar Pasta**, navegue até uma pasta que contenha os arquivos .txt e, em seguida, selecione a pasta e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d653-153">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="9d653-154">A `ListBox` contém uma lista de arquivos .txt na pasta selecionada.</span><span class="sxs-lookup"><span data-stu-id="9d653-154">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="9d653-155">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-155">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="9d653-156">Para obter atributos de um arquivo e o conteúdo de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="9d653-156">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="9d653-157">Criar um manipulador de eventos `Click` para `examineButton`, clicando duas vezes no controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="9d653-157">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="9d653-158">Adicione o seguinte código ao manipulador de eventos do `Click`.</span><span class="sxs-lookup"><span data-stu-id="9d653-158">Add the following code to the `Click` event handler.</span></span>  
  
     <span data-ttu-id="9d653-159">[!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-159">[!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]</span></span>  
  
     <span data-ttu-id="9d653-160">O código verifica se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9d653-160">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="9d653-161">Então, ele obtém a entrada de caminho do arquivo da `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9d653-161">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="9d653-162">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> é usado para verificar se o arquivo ainda existe.</span><span class="sxs-lookup"><span data-stu-id="9d653-162">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="9d653-163">O caminho do arquivo será enviado como um argumento para o método `GetTextForOutput`, que será adicionado na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="9d653-163">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="9d653-164">Esse método retorna uma cadeia de caracteres que contém informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d653-164">This method returns a string that contains file information.</span></span> <span data-ttu-id="9d653-165">As informações do arquivo aparecem em uma **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="9d653-165">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="9d653-166">Adicione o seguinte método `GetTextForOutput`.</span><span class="sxs-lookup"><span data-stu-id="9d653-166">Add the following `GetTextForOutput` method.</span></span>  
  
     <span data-ttu-id="9d653-167">[!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-167">[!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]</span></span>  
  
     <span data-ttu-id="9d653-168">O código usa o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> para obter parâmetros do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d653-168">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="9d653-169">Os parâmetros do arquivo são adicionados a um <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="9d653-169">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="9d653-170">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lê o conteúdo do arquivo em um <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="9d653-170">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="9d653-171">A primeira linha do conteúdo é obtida de `StreamReader` e é adicionada no `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="9d653-171">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="9d653-172">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-172">Run the application.</span></span> <span data-ttu-id="9d653-173">Clique em **Procurar** e navegue até uma pasta que contenha os arquivos .txt.</span><span class="sxs-lookup"><span data-stu-id="9d653-173">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="9d653-174">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d653-174">Click **OK**.</span></span>  
  
     <span data-ttu-id="9d653-175">Selecione um arquivo na `ListBox` e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="9d653-175">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="9d653-176">Uma `MessageBox` mostra as informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d653-176">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="9d653-177">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-177">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="9d653-178">Para adicionar uma entrada de log</span><span class="sxs-lookup"><span data-stu-id="9d653-178">To add a log entry</span></span>  
  
1.  <span data-ttu-id="9d653-179">Adicione o seguinte código ao final do manipulador de eventos de `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="9d653-179">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     <span data-ttu-id="9d653-180">[!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-180">[!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]</span></span>  
  
     <span data-ttu-id="9d653-181">O código define o caminho do arquivo de log, a fim de colocar o arquivo de log no mesmo diretório que o arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="9d653-181">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="9d653-182">O texto da entrada de log é definido com a data e hora atuais, seguido pelas informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d653-182">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="9d653-183">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, com o argumento `append` definido como `True`, é usado para criar a entrada de log.</span><span class="sxs-lookup"><span data-stu-id="9d653-183">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="9d653-184">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-184">Run the application.</span></span> <span data-ttu-id="9d653-185">Navegue até um arquivo de texto, selecione-o na `ListBox`, escolha a caixa de seleção **Salvar Resultados** e, em seguida, clique em **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="9d653-185">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="9d653-186">Verifique se a entrada de log foi gravada para o arquivo `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="9d653-186">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="9d653-187">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-187">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="9d653-188">Para usar o diretório atual</span><span class="sxs-lookup"><span data-stu-id="9d653-188">To use the current directory</span></span>  
  
1.  <span data-ttu-id="9d653-189">Crie um manipulador de eventos para `Form1_Load`, clicando duas vezes no formulário.</span><span class="sxs-lookup"><span data-stu-id="9d653-189">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="9d653-190">Adicione o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9d653-190">Add the following code to the event handler.</span></span>  
  
     <span data-ttu-id="9d653-191">[!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-191">[!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]</span></span>  
  
     <span data-ttu-id="9d653-192">Esse código define o diretório padrão do navegador de pastas para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9d653-192">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="9d653-193">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-193">Run the application.</span></span> <span data-ttu-id="9d653-194">Quando você clica em **Procurar** pela primeira vez, a caixa de diálogo **Procurar Pasta** é aberta no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9d653-194">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="9d653-195">Interromper a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-195">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="9d653-196">Para habilitar controles de maneira seletiva</span><span class="sxs-lookup"><span data-stu-id="9d653-196">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="9d653-197">Adicione o seguinte método `SetEnabled`.</span><span class="sxs-lookup"><span data-stu-id="9d653-197">Add the following `SetEnabled` method.</span></span>  
  
     <span data-ttu-id="9d653-198">[!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-198">[!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]</span></span>  
  
     <span data-ttu-id="9d653-199">O método `SetEnabled` habilita ou desabilita os controles, dependendo se um item está selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9d653-199">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="9d653-200">Criar um manipulador de eventos `SelectedIndexChanged` para `filesListBox`, clicando duas vezes no controle `ListBox` no formulário.</span><span class="sxs-lookup"><span data-stu-id="9d653-200">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="9d653-201">Adicione uma chamada para `SetEnabled` no novo manipulador de eventos `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="9d653-201">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="9d653-202">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="9d653-202">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="9d653-203">Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="9d653-203">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="9d653-204">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d653-204">Run the application.</span></span> <span data-ttu-id="9d653-205">A caixa de seleção **Salvar Resultados** e o botão **Examinar** ficarão desabilitados se um item não for selecionado na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9d653-205">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="9d653-206">Exemplo completo usando My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="9d653-206">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="9d653-207">A seguir está o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="9d653-207">Following is the complete example.</span></span>  
  
 <span data-ttu-id="9d653-208">[!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-208">[!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]</span></span>  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="9d653-209">Exemplo completo usando System.IO</span><span class="sxs-lookup"><span data-stu-id="9d653-209">Full example using System.IO</span></span>  
 <span data-ttu-id="9d653-210">O exemplo equivalente a seguir usa classes do namespace <xref:System.IO> em vez de usar objetos `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="9d653-210">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 <span data-ttu-id="9d653-211">[!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="9d653-211">[!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d653-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d653-212">See Also</span></span>  
 <span data-ttu-id="9d653-213"><xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="9d653-213"><xref:System.IO></span></span>   
 <span data-ttu-id="9d653-214"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="9d653-214"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="9d653-215"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="9d653-215"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A></span></span>   
 [<span data-ttu-id="9d653-216">Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d653-216">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

