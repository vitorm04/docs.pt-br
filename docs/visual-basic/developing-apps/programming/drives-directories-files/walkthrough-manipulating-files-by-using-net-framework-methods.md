---
title: "Instru&#231;&#245;es passo a passo: manipulando arquivos usando m&#233;todos do .NET Framework (Visual Basic) | Microsoft Docs"
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
  - "Arquivos , acessando"
  - "Arquivos , procurando"
  - "E/S [Visual Basic], lendo texto de arquivos"
  - "E/S [Visual Basic], explicações passo a passo"
  - "E/S [Visual Basic], escrevendo texto em arquivos"
  - "lendo arquivos de texto"
  - "Classe StreamReader, explicações passo a passo"
  - "Classe StreamWriter, explicações passo a passo"
  - "arquivos de texto, lendo"
  - "arquivos de texto, gravando em"
  - "texto, escrevendo em arquivos"
  - "escrevendo em arquivos, explicações passo a passo"
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: manipulando arquivos usando m&#233;todos do .NET Framework (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Essa explicação passo a passo demonstra como abrir e ler um arquivo usando a classe <xref:System.IO.StreamReader>, verificar para ver se um arquivo está sendo acessado, procurar uma sequência de caracteres dentro de uma leitura de arquivo com uma instância da classe <xref:System.IO.StreamReader> e escrever para um arquivo usando a classe <xref:System.IO.StreamWriter>.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## Criando o aplicativo  
 Inicie o [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] e comece o projeto, criando um formulário que o usuário pode usar para gravar no arquivo designado.  
  
#### Para criar o projeto  
  
1.  No menu **File**, selecione **New Project**.  
  
2.  No painel **New Project**, clique em **Windows Application**.  
  
3.  Na caixa **Name** digite `MyDiary` e clique **OK**.  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] adiciona o projeto para o **Solution Explorer**, e abre o **Windows Forms Designer**.  
  
4.  Adicione os controles na tabela a seguir para o formulário e defina os valores correspondentes para suas propriedades.  
  
||||  
|-|-|-|  
|**Object**|**Propriedades**|**Valor**|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`Enviar`<br /><br /> Enviar entrada|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`Limpar`<br /><br /> Limpar entrada|  
|<xref:System.Windows.Forms.TextBox>|**Nome**<br /><br /> **Texto**<br /><br /> **Multiline \(de múltiplas linhas\)**|`Entrada`<br /><br /> Digite alguma coisa.<br /><br /> `False`|  
  
## Gravando no arquivo  
 Para adicionar a capacidade de gravar em um arquivo por meio do aplicativo, use o <xref:System.IO.StreamWriter> classe.  <xref:System.IO.StreamWriter>destina\-se a saída de caractere em uma codificação específica, enquanto o <xref:System.IO.Stream> classe foi criada para bytes de entrada e saída.  Use <xref:System.IO.StreamWriter> para gravar linhas de informações em um padrão arquivo de texto.  Para obter mais informações sobre o <xref:System.IO.StreamWriter> da classe, consulte <xref:System.IO.StreamWriter>.  
  
#### Para adicionar a funcionalidade da gravação  
  
1.  No menu **View**, escolha **Code** para abrir o Editor de Código.  
  
2.  Como o aplicativo se refere ao namespace<xref:System.IO>, adicione as instruções a seguir ao início do seu código, antes da declaração de classe para o formulário, que inicia `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     Antes de gravar no arquivo, você deve criar uma instância de uma classe <xref:System.IO.StreamWriter>.  
  
3.  Do menu **View**, escolha **Designer** para retornar ao **Windows Forms Designer**.  Clique duas vezes no botão `Submit` para criar um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão e em seguida, adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  O Visual Studio Integrated Development Environment \(IDE\) retorna para o editor de códigos e posiciona o ponto de inserção com o manipulador de eventos, onde você deve adicionar o código.  
  
1.  Para escrever no arquivo, use o método <xref:System.IO.StreamWriter.Write%2A> da classe <xref:System.IO.StreamWriter>.  Adicione o código a seguir diretamente após `Dim fw As StreamWriter`.  Você não precisará se preocupar com que uma exceção será ser gerada se o arquivo não for encontrado, porque ele vai ser criado se ele ainda não existir.  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  Certifique\-se que o usuário não pode enviar uma entrada em branco adicionando o código a seguir diretamente após `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  Como isto é uma diário, o usuário desejará atribuir uma data para cada entrada.  Insira o código a seguir após `fw = New StreamWriter("C:\MyDiary.txt", True)` para definir a variável `Today` como a data atual.  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  Finalmente, anexe o código para limpar a <xref:System.Windows.Forms.TextBox>.  Adicione o seguinte código para o botão `Clear` do evento <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## Adicionar recursos de exibição ao Diário  
 Nesta seção, você adiciona um recurso que exibe a entrada mais recente em `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  Você também pode adicionar um <xref:System.Windows.Forms.ComboBox> que exibe várias entradas e na qual um usuário pode selecionar uma entrada para exibir em `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  Uma instância da classe <xref:System.IO.StreamReader> lê de `MyDiary.txt`.  Como a classe <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader> destina\-se ao uso com arquivos de texto.  
  
 Para essa seção de explicação passo a passo, adicione os controles na tabela a seguir para o formulário e defina os valores correspondentes para suas propriedades.  
  
|Controle|Propriedades|Valores|  
|--------------|------------------|-------------|  
|<xref:System.Windows.Forms.TextBox>|**Nome**<br /><br /> **Visible**<br /><br /> **Tamanho**<br /><br /> **Multiline \(de múltiplas linhas\)**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`Exibir`<br /><br /> Exibir|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`GetEntries`<br /><br /> Obter entradas|  
|<xref:System.Windows.Forms.ComboBox>|**Nome**<br /><br /> **Texto**<br /><br /> **Enabled**|`PickEntries`<br /><br /> Selecione uma entrada<br /><br /> `False`|  
  
#### Para preencher a combo box  
  
1.  O `PickEntries` <xref:System.Windows.Forms.ComboBox> é usado para exibir as datas em que um usuário envia cada entrada, para que o usuário possa selecionar uma entrada a partir de uma data específica.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `GetEntries` e adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  Para testar seu código, pressione F5 para compilar o aplicativo e clique **Get Entries**.  Clique na seta suspensa em <xref:System.Windows.Forms.ComboBox> para exibir as datas de entrada.  
  
#### Para escolher e exibir entradas individuais  
  
1.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `Display` e adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  Para testar seu código, pressione F5 para compilar o aplicativo e depois envie uma entrada.  Clique em **Get Entries**, selecione uma entrada de <xref:System.Windows.Forms.ComboBox>, e então clique **Display**.  O conteúdo da entrada selecionada aparece em `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## Habilitando usuários para excluir ou modificar entradas  
 Finalmente, você pode incluir funcionalidade adicional permitindo aos usuários excluir ou modificar uma entrada, utilizando os botões `DeleteEntry` e `EditEntry`.  Os dois botões permanecem desativados a menos que uma entrada seja exibida.  
  
 Adicione os controles na tabela a seguir para o formulário e defina os valores correspondentes para suas propriedades.  
  
|Controle|Propriedades|Valores|  
|--------------|------------------|-------------|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**<br /><br /> **Enabled**|`DeleteEntry`<br /><br /> Excluir entrada<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**<br /><br /> **Enabled**|`EditEntry`<br /><br /> Editar entrada<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**<br /><br /> **Enabled**|`SubmitEdit`<br /><br /> Enviar editar<br /><br /> `False`|  
  
#### Para permitir a exclusão e modificação de entradas  
  
1.  Adicione o seguinte código para o botão `Display` do evento <xref:System.Windows.Forms.Control.Click>, depois de `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `DeleteEntry` e adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  Quando um usuário exibe uma entrada, o botão `EditEntry` se torna ativado.  Adicione o seguinte código para o evento <xref:System.Windows.Forms.Control.Click> do botão `Display`, depois de `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `EditEntry` e adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `SubmitEdit` e adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 Para testar seu código, pressione F5 para compilar o aplicativo.  Clique em **Get Entries**, selecione uma entrada e clique **Display**.  A entrada aparece em `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  Clique em **Edit Entry**.  A entrada aparece em `Entry` <xref:System.Windows.Forms.TextBox>.  Edite a entrada na caixa `Entry` <xref:System.Windows.Forms.TextBox> e clique em **Submit Edit** .  Abra o arquivo `MyDiary.txt` para confirmar a correção.  Agora, selecione uma entrada e clique em **Delete Entry**.  Quando o <xref:System.Windows.Forms.MessageBox> solicita confirmação, clique em  **OK** .  Feche o aplicativo e abra `MyDiary.txt` para confirmar a exclusão.  
  
## Consulte também  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamWriter>   
 [Explicações Passo\-a\-passo](../../../../visual-basic/walkthroughs.md)