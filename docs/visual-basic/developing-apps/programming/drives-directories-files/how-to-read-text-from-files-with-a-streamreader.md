---
title: "Como ler texto a partir de arquivos com um StreamReader (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Arquivos , lendo"
  - "lendo arquivos, texto"
  - "lendo texto de arquivos"
  - "texto, lendo de arquivos"
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler texto a partir de arquivos com um StreamReader (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `My.Computer.FileSystem` fornece métodos para abrir um <xref:System.IO.TextReader> e um <xref:System.IO.TextWriter>.  Esses métodos, `OpenTextFileWriter` e `OpenTextFileReader`, são métodos avançados que não são exibidos no IntelliSense a menos que você selecione a guia **All** .  
  
### Para ler uma linha de um arquivo com um leitor de texto  
  
-   Use o método `OpenTextFileReader` para abrir o <xref:System.IO.TextReader>, especificando o arquivo.  Este exemplo abre o arquivo chamado `testfile.txt`, lê uma linha a partir dele, e exibe a linha em uma caixa de mensagem.  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## Programação robusta  
 O arquivo que é lido deve ser um arquivo de texto.  
  
 Não faça decisões sobre o conteúdo do arquivo com base no nome do arquivo.  Por exemplo, o arquivo Form1.vb pode não ser um arquivo fonte do Visual Basic.  
  
 Verifique todas as entradas antes de usar os dados no seu aplicativo.  O conteúdo do arquivo pode não ser esperado e métodos para ler o arquivo podem falhar.  
  
## Segurança do .NET Framework  
 Para ler de um arquivo, seu assembly requer um nível de privilégio concedido pela classe <xref:System.Security.Permissions.FileIOPermission>.  Se você estiver executando em um contexto parcialmente confiável, o código pode lançar uma exceção devido a privilégios insuficientes.  Para obter mais informações, consulte [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md).  O usuário também precisa acessar o arquivo.  Para obter mais informações, consulte [ACL Technology Overview](http://msdn.microsoft.com/pt-br/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:System.Windows.Forms.OpenFileDialog>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>   
 [Componente SaveFileDialog](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md)   
 [Lendo a partir de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)