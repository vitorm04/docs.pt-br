---
title: "Como gravar texto em arquivos no diretório Meus Documentos no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a756be7f61c812269d5ee08d99ccf6785ddcc7df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Como gravar texto em arquivos no diretório Meus Documentos no Visual Basic
O objeto `My.Computer.FileSystem.SpecialDirectories` permite que você acesse diretórios especiais, como o diretório **MyDocuments**.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Para gravar novos arquivos de texto no diretório Meus Documentos  
  
1.  Use a propriedade `My.Computer.FileSystem.SpecialDirectories.MyDocuments` para fornecer o caminho.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Use o método `WriteAllText` para escrever o texto no arquivo especificado.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Substitua `test.txt` pelo nome do arquivo no qual você deseja gravar.  
  
## <a name="robust-programming"></a>Programação robusta  
 Esse código lança novamente todas as exceções que podem ocorrer ao gravar texto no arquivo. É possível reduzir a probabilidade de exceções usando controles do Windows Forms como os componentes [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) que limitam as escolhas do usuário para validar nomes de arquivo. No entanto, o uso desses controles não é à prova de falhas. O sistema de arquivos pode ser alterado entre o momento em que o usuário seleciona um arquivo e o momento em que o código é executado. Portanto, o tratamento de exceções é quase sempre é necessário ao trabalhar com arquivos.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você estiver executando em um contexto de confiança parcial, o código pode gerar uma exceção devido a privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../framework/misc/code-access-security-basics.md).  
  
 Esse exemplo cria um novo arquivo. Se um aplicativo precisar criar um arquivo, esse aplicativo precisará da permissão de criação para a pasta. As permissões são definidas usando listas de controle de acesso. Se o arquivo já existir, o aplicativo precisará somente da permissão de gravação, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder privilégios de leitura para um único arquivo, em vez de conceder privilégios de criação para uma pasta. Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta **Arquivos de Programas**. Para obter mais informações, consulte [Visão Geral da Tecnologia de ACL](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
