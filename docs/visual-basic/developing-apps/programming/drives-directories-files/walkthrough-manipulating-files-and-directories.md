---
title: "Manipulando arquivos e diretórios no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd1e61503394741e7943d30d383f2e7c5ea35f68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic
Este passo a passo fornece uma introdução aos fundamentos de E/S de arquivo no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Ele descreve como criar um pequeno aplicativo que lista e examina os arquivos de texto em um diretório. Para cada arquivo de texto selecionado, o aplicativo fornece atributos de arquivo e a primeira linha do conteúdo. Há uma opção para gravar as informações em um arquivo de log.  
  
 Este passo a passo usa os membros de `My.Computer.FileSystem Object`, que estão disponível em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Consulte <xref:Microsoft.VisualBasic.FileIO.FileSystem> para obter mais informações. No final do passo a passo, será fornecido um exemplo equivalente que usa classes do namespace <xref:System.IO>.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  No menu **Arquivo**, clique em **Novo Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  No painel **Modelos Instalados**, expanda **Visual Basic** e, em seguida, selecione **Windows**. No meio do painel **Modelos**, clique em **Aplicativo do Windows Forms**.  
  
3.  Na caixa **Nome**, digite `FileExplorer` para definir o nome do projeto e, em seguida, clique em **OK**.  
  
     O [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adiciona o projeto ao **Gerenciador de Soluções** e o Designer de Formulários do Windows é aberto.  
  
4.  Adicione os controles da tabela a seguir no formulário e defina os valores correspondentes para as respectivas propriedades.  
  
    |Controle|Propriedade|Valor|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Nome**|`filesListBox`|  
    |**Button**|**Nome**<br /><br /> **Texto**|`browseButton`<br /><br /> **Procurar**|  
    |**Button**|**Nome**<br /><br /> **Texto**|`examineButton`<br /><br /> **Examinar**|  
    |**CheckBox**|**Nome**<br /><br /> **Texto**|`saveCheckBox`<br /><br /> **Salvar resultados**|  
    |**FolderBrowserDialog**|**Nome**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Para selecionar uma pasta e listar arquivos em uma pasta  
  
1.  Criar um manipulador de eventos `Click` para `browseButton`, clicando duas vezes no controle no formulário. O Editor de Códigos é aberto.  
  
2.  Adicione o seguinte código ao manipulador de eventos do `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     A chamada `FolderBrowserDialog1.ShowDialog` abre a caixa de diálogo **Procurar Pasta**. Após o usuário clicar em **OK**, a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> será enviada como um argumento para o método `ListFiles`, que será adicionado na próxima etapa.  
  
3.  Adicione o seguinte método `ListFiles`.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Primeiro, esse código limpa a **ListBox**.  
  
     Depois, o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> recupera uma coleção de cadeias de caracteres, uma para cada arquivo do diretório. O método `GetFiles` aceita um argumento de padrão de pesquisa para recuperar os arquivos que correspondem a um padrão específico. Neste exemplo, somente os arquivos que têm a extensão .txt serão retornados.  
  
     As cadeias de caracteres retornadas pelo método `GetFiles` serão adicionadas à **ListBox**.  
  
4.  Execute o aplicativo. Clique no botão **Procurar**. Na caixa de diálogo **Procurar Pasta**, navegue até uma pasta que contenha os arquivos .txt e, em seguida, selecione a pasta e clique em **OK**.  
  
     A `ListBox` contém uma lista de arquivos .txt na pasta selecionada.  
  
5.  Interromper a execução do aplicativo.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Para obter atributos de um arquivo e o conteúdo de um arquivo de texto  
  
1.  Criar um manipulador de eventos `Click` para `examineButton`, clicando duas vezes no controle no formulário.  
  
2.  Adicione o seguinte código ao manipulador de eventos do `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     O código verifica se um item está selecionado na `ListBox`. Então, ele obtém a entrada de caminho do arquivo da `ListBox`. O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> é usado para verificar se o arquivo ainda existe.  
  
     O caminho do arquivo será enviado como um argumento para o método `GetTextForOutput`, que será adicionado na próxima etapa. Esse método retorna uma cadeia de caracteres que contém informações do arquivo. As informações do arquivo aparecem em uma **MessageBox**.  
  
3.  Adicione o seguinte método `GetTextForOutput`.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     O código usa o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> para obter parâmetros do arquivo. Os parâmetros do arquivo são adicionados a um <xref:System.Text.StringBuilder>.  
  
     O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lê o conteúdo do arquivo em um <xref:System.IO.StreamReader>. A primeira linha do conteúdo é obtida de `StreamReader` e é adicionada no `StringBuilder`.  
  
4.  Execute o aplicativo. Clique em **Procurar** e navegue até uma pasta que contenha os arquivos .txt. Clique em **OK**.  
  
     Selecione um arquivo na `ListBox` e, em seguida, clique em **Examinar**. Uma `MessageBox` mostra as informações do arquivo.  
  
5.  Interromper a execução do aplicativo.  
  
### <a name="to-add-a-log-entry"></a>Para adicionar uma entrada de log  
  
1.  Adicione o seguinte código ao final do manipulador de eventos de `examineButton_Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     O código define o caminho do arquivo de log, a fim de colocar o arquivo de log no mesmo diretório que o arquivo selecionado. O texto da entrada de log é definido com a data e hora atuais, seguido pelas informações do arquivo.  
  
     O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, com o argumento `append` definido como `True`, é usado para criar a entrada de log.  
  
2.  Execute o aplicativo. Navegue até um arquivo de texto, selecione-o na `ListBox`, escolha a caixa de seleção **Salvar Resultados** e, em seguida, clique em **Examinar**. Verifique se a entrada de log foi gravada para o arquivo `log.txt`.  
  
3.  Interromper a execução do aplicativo.  
  
### <a name="to-use-the-current-directory"></a>Para usar o diretório atual  
  
1.  Crie um manipulador de eventos para `Form1_Load`, clicando duas vezes no formulário.  
  
2.  Adicione o seguinte código ao manipulador de eventos.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Esse código define o diretório padrão do navegador de pastas para o diretório atual.  
  
3.  Execute o aplicativo. Quando você clica em **Procurar** pela primeira vez, a caixa de diálogo **Procurar Pasta** é aberta no diretório atual.  
  
4.  Interromper a execução do aplicativo.  
  
### <a name="to-selectively-enable-controls"></a>Para habilitar controles de maneira seletiva  
  
1.  Adicione o seguinte método `SetEnabled`.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     O método `SetEnabled` habilita ou desabilita os controles, dependendo se um item está selecionado na `ListBox`.  
  
2.  Criar um manipulador de eventos `SelectedIndexChanged` para `filesListBox`, clicando duas vezes no controle `ListBox` no formulário.  
  
3.  Adicione uma chamada para `SetEnabled` no novo manipulador de eventos `filesListBox_SelectedIndexChanged`.  
  
4.  Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `browseButton_Click`.  
  
5.  Adicione uma chamada para `SetEnabled` ao final do manipulador de eventos `Form1_Load`.  
  
6.  Execute o aplicativo. A caixa de seleção **Salvar Resultados** e o botão **Examinar** ficarão desabilitados se um item não for selecionado na `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Exemplo completo usando My.Computer.FileSystem  
 A seguir está o exemplo completo.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>Exemplo completo usando System.IO  
 O exemplo equivalente a seguir usa classes do namespace <xref:System.IO> em vez de usar objetos `My.Computer.FileSystem`.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
