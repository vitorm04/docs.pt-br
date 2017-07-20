---
title: Como Ler Texto de Arquivos com um StreamReader (Visual Basic) | Microsoft Docs
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
- reading files, text
- text, reading from files
- reading text from files
- files, reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: e53fe99a3b3292fc465271d667ef76053e61af51
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Como ler texto a partir de arquivos com um StreamReader (Visual Basic)
O objeto `My.Computer.FileSystem` fornece métodos para abrir um <xref:System.IO.TextReader> e um <xref:System.IO.TextWriter>. Esses métodos, `OpenTextFileWriter` e `OpenTextFileReader`, são métodos avançados que não aparecem no IntelliSense a menos que a guia **Todos** seja selecionada.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Ler uma linha de um arquivo com um leitor de texto  
  
-   Use o método `OpenTextFileReader` para abrir o <xref:System.IO.TextReader>, especificando o arquivo. Esse exemplo abre o arquivo chamado `testfile.txt`, lê uma linha dele e exibe a linha em uma caixa de mensagem.  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 O arquivo lido deve ser um arquivo de texto.  
  
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.  
  
 Verifique todas as entradas antes de usar os dados no seu aplicativo. O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para ler de um arquivo, seu assembly requer um nível de privilégio concedido pela classe <xref:System.Security.Permissions.FileIOPermission>. Se você estiver executando em um contexto de confiança parcial, o código pode gerar uma exceção devido a privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8). O usuário também precisa de acesso ao arquivo. Para obter mais informações, consulte [Visão Geral da Tecnologia de ACL](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:System.Windows.Forms.OpenFileDialog>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>   
 [Componente SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)   
 [Leitura de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
