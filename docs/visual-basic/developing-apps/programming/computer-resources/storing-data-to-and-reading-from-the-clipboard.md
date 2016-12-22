---
title: "Armazenando dados e lendo a partir da &#193;rea de Transfer&#234;ncia (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Área de Transferência"
  - "Área de Transferência, lendo de (My.Computer.Clipboard)"
  - "Área de Transferência, armazenando dados em (My.Computer.Clipboard)"
  - "dados [Visual Basic], Área de Transferência"
  - "Objeto My.Computer.Clipboard, tarefas"
  - "lendo dados, da Área de Transferência"
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Armazenando dados e lendo a partir da &#193;rea de Transfer&#234;ncia (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A área de transferência pode ser usada para armazenar dados, como textos e imagens.  Como a Área de transferência é compartilhada com todos os processos ativos, ela pode ser usada para transferir dados entre eles.  O `My.Computer.Clipboard` objeto permite que você acesse facilmente a área de transferência e ler e gravar nela.  
  
## Leitura da área de transferência  
 Use o <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> método para ler o texto na área de transferência.  O código a seguir lê o texto e o exibe em uma caixa de mensagem.  É preciso que haja texto armazenado na área de transferência para que o exemplo seja executado corretamente.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador de trechos de código, ele está localizado em **Windows Forms Applications \> Clipboard**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> para recuperar uma imagem da área de transferência.  Este exemplo verifica se há alguma imagem na Área de transferência antes de recuperá\-la e atribuí\-la a  `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador de trechos de código, ele está localizado em **Windows Forms Applications \> Clipboard**.Para obter mais informações, consulte: [Trechos de código](/visual-studio/ide/code-snippets)..  
  
 Itens colocados na Área de transferência persistirão mesmo após o aplicativo ser encerrado.  
  
## Determinando o tipo de arquivo armazenado na área de transferência  
 Dados na área de transferência podem ser um número de diferentes formulários, como texto, um arquivo de áudio ou uma imagem.  Em ordem para determinar que tipo de arquivo está na área de transferência, você pode usar métodos como <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>,<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>,<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> e <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.  O método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> pode ser usado se você tiver um formato personalizado que você deseja verificar.  
  
 Use a função `ContainsImage` para determinar se os dados contidos na área de transferência são uma imagem.  O código a seguir verifica para ver se os dados é uma imagem e relatórios de acordo.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## Limpando a área de transferência.  
 O <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> método limpa a área de transferência.  Como a Área de transferência é compartilhada por outros processos, limpá\-la pode ter um impacto nesses processos.  
  
 O código a seguir mostra como usar o `Clear` método.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## Escrever para a área de transferência.  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> para escrever texto na Área de transferência.  O código a seguir grava a cadeia de caracteres "This is a test string" na Área de Transferência.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 O `SetText` método pode aceitar um parâmetro de formato que contém um tipo de <xref:System.Windows.Forms.TextDataFormat>.  O código a seguir grava a cadeia de caracteres "This is a test string" na Área de Transferência como texto RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> para escrever dados na Área de transferência.  Este exemplo grava a `DataObject` `dataChunk` na Área de transferência no formato personalizado`specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> para escrever dados de áudio na Área de transferência.  Este exemplo cria a matriz de bytes `musicReader`, lê o arquivo `cool.wav` nela e o coloca na Área de transferência.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Como a área de transferência pode ser acessada por outros usuários, não a use para armazenar informações confidenciais, como senhas ou dados confidenciais.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [Como ler dados de objeto a partir de um arquivo XML](../Topic/How%20to:%20Read%20Object%20Data%20from%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como gravar dados de objeto em um arquivo XML](../Topic/How%20to:%20Write%20Object%20Data%20to%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)