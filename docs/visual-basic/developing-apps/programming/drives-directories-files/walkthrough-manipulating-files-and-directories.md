---
title: "Instru&#231;&#245;es passo a passo: manipulando arquivos e diret&#243;rios no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "acesso a arquivos, explicações passo a passo"
  - "Arquivos , lendo texto"
  - "Arquivos , gravando texto"
  - "E/S [Visual Basic], lendo texto de arquivos"
  - "E/S [Visual Basic], explicações passo a passo"
  - "E/S [Visual Basic], escrevendo texto em arquivos"
  - "lendo arquivos, texto"
  - "lendo texto de arquivos, explicações passo a passo"
  - "texto, lendo de arquivos"
  - "texto, escrevendo em arquivos"
  - "código do Visual Basic, acesso a arquivos"
  - "escrevendo em arquivos, explicações passo a passo"
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
caps.handback.revision: 49
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: manipulando arquivos e diret&#243;rios no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta explicação passo a passo fornece uma introdução para os fundamentos de E\/S de arquivos no  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Ele descreve como criar um pequeno aplicativo que lista e examina os arquivos de texto em um diretório.  Para cada arquivo de texto selecionado, o aplicativo fornece atributos de arquivo e a primeira linha do conteúdo.  Há uma opção para gravar informações em um arquivo de log.  
  
 Esta explicação passo a passo usa membros da `My.Computer.FileSystem Object`, que estão disponíveis em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Consulte <xref:Microsoft.VisualBasic.FileIO.FileSystem> para obter mais informações.  No final da explicação, é um exemplo equivalente desde que usa as classes da <xref:System.IO> espaço para nome.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar o projeto  
  
1.  No menu **File**, clique em **New Project**.  
  
     A caixa de diálogo **New Project** será exibida.  
  
2.  No  **Modelos instalados** painel, expanda  **Visual Basic**e, em seguida, clique em  **Windows**.  No  **modelos de** no meio, clique em Painel de  **Windows Forms Application**.  
  
3.  No  **nome** , digite  `FileExplorer` para definir o nome do projeto e, em seguida, clique em  **OK**.  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] adiciona o projeto para o **Solution Explorer** e o Windows Forms Designer é aberto.  
  
4.  Adicione os controles na tabela a seguir para o formulário e defina os valores correspondentes para suas propriedades.  
  
    |Controle|Propriedade|Valor|  
    |--------------|-----------------|-----------|  
    |**ListBox**|**Nome**|`filesListBox`|  
    |**Button**|**Nome**<br /><br /> **Texto**|`browseButton`<br /><br /> Browse|  
    |**Button**|**Nome**<br /><br /> **Texto**|`examineButton`<br /><br /> Examinar|  
    |**CheckBox**|**Nome**<br /><br /> **Texto**|`saveCheckBox`<br /><br /> Salvar resultados|  
    |**FolderBrowserDialog**|**Nome**|`FolderBrowserDialog1`|  
  
### Selecione uma pasta e listar arquivos em uma pasta  
  
1.  Criar um `Click` manipulador de eventos para `browseButton` , clicando duas vezes no controle no formulário.  Code Editor aparece.  
  
2.  Adicione o seguinte código para o manipulador de eventos `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     O `FolderBrowserDialog1.ShowDialog` abre de chamar o  **Procurar pasta** caixa de diálogo.  Depois que o usuário clica em  **OK**, o <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade é enviada como um argumento para o `ListFiles` método, que é adicionado na próxima etapa.  
  
3.  Adicione o seguinte `ListFiles` método.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Este código primeiro limpa a  **caixa de listagem**.  
  
     O <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> método recupera uma coleção de seqüências de caracteres, uma para cada arquivo no diretório.  O `GetFiles` método aceita um argumento de padrão de pesquisa para recuperar arquivos que correspondem a um determinado padrão.  Neste exemplo, somente os arquivos que possuem a extensão. txt são retornados.  
  
     Seqüências de caracteres que são retornadas pelo `GetFiles` método, em seguida, são adicionados para o  **ListBox**.  
  
4.  Execute o aplicativo.  Clique no botão **Browse**.  No  **Procurar pasta** caixa de diálogo, navegue até uma pasta que contém os arquivos. txt e, em seguida, selecione a pasta e clique em  **OK**.  
  
     O `ListBox` contém uma lista de arquivos. txt na pasta selecionada.  
  
5.  Pare a execução do aplicativo.  
  
### Para obter os atributos de um arquivo e conteúdo de um arquivo de texto  
  
1.  Criar um `Click` manipulador de eventos para `examineButton` , clicando duas vezes no controle no formulário.  
  
2.  Adicione o seguinte código para o manipulador de eventos `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     O código verifica se um item é selecionado na `ListBox`.  Ele então obtém a entrada de caminho do arquivo da `ListBox`.  O <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> método é usado para verificar se o arquivo ainda existe.  
  
     O caminho do arquivo é enviado como um argumento para o `GetTextForOutput` método, que é adicionado na próxima etapa.  Esse método retorna uma seqüência de caracteres que contém informações sobre o arquivo.  As informações do arquivo aparecem em um  **MessageBox**.  
  
3.  Adicione o seguinte `GetTextForOutput` método.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     O código usa a <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> método para obter os parâmetros de arquivo.  Os parâmetros do arquivo são adicionados a um <xref:System.Text.StringBuilder>.  
  
     O <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> método lê o conteúdo do arquivo em um <xref:System.IO.StreamReader>.  A primeira linha do conteúdo é obtida a partir do `StreamReader` e é adicionado ao `StringBuilder`.  
  
4.  Execute o aplicativo.  Clique em  **Procurar**e navegue até uma pasta que contém os arquivos. txt.  Clique em **OK**.  
  
     Selecione um arquivo na `ListBox`e, em seguida, clique em  **Examine**.  A `MessageBox` mostra as informações do arquivo.  
  
5.  Pare a execução do aplicativo.  
  
### Para adicionar uma entrada de log  
  
1.  Adicione o seguinte código ao final da `examineButton_Click` manipulador de eventos.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     O código define o caminho do arquivo de log para colocar o arquivo de log no mesmo diretório do arquivo selecionado.  O texto da entrada do log é definido como a data e hora atuais seguido as informações do arquivo.  
  
     O <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> método, com o `append` argumento definido como `True`, é usado para criar a entrada de log.  
  
2.  Execute o aplicativo.  Vá para um arquivo de texto, selecioná\-lo na `ListBox`, selecione o  **Salvar resultados** caixa de seleção e, em seguida, clique em  **Examine**.  Verifique se que a entrada de log é gravada para o `log.txt` arquivo.  
  
3.  Pare a execução do aplicativo.  
  
### Para usar o diretório atual  
  
1.  Crie um manipulador de eventos para `Form1_Load` clicando duas vezes no formulário.  
  
2.  Adicione o seguinte código ao manipulador de eventos.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Este código define o diretório padrão do navegador da pasta para a pasta atual.  
  
3.  Execute o aplicativo.  Quando você clica em  **Procurar** na primeira vez, o  **Procurar pasta** caixa de diálogo é aberta para o diretório atual.  
  
4.  Pare a execução do aplicativo.  
  
### Para ativar seletivamente os controles  
  
1.  Adicione o seguinte `SetEnabled` método.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     O `SetEnabled` método ativa ou desativa os controles, dependendo se um item é selecionado na `ListBox`.  
  
2.  Criar um `SelectedIndexChanged` manipulador de eventos para `filesListBox` , clicando duas vezes o `ListBox` controle no formulário.  
  
3.  Adicione uma chamada para `SetEnabled` nos novos `filesListBox_SelectedIndexChanged` manipulador de eventos.  
  
4.  Adicione uma chamada para `SetEnabled` no final do `browseButton_Click` manipulador de eventos.  
  
5.  Adicione uma chamada para `SetEnabled` no final do `Form1_Load` manipulador de eventos.  
  
6.  Execute o aplicativo.  O  **Salvar resultados** caixa de seleção e o  **Examine** botão está desabilitado se um item não estiver selecionado na `ListBox`.  
  
## Exemplo completo usando My.Computer.FileSystem  
 Veja a seguir o exemplo completo.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## Exemplo completo usando System. IO  
 O exemplo a seguir equivalente usa as classes da <xref:System.IO> espaço para nome em vez de usar `My.Computer.FileSystem` objetos.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## Consulte também  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)