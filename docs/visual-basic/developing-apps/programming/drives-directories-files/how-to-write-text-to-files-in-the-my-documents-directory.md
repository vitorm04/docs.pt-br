---
title: "Como gravar texto em arquivos no diret&#243;rio Meus Documentos no Visual Basic | Microsoft Docs"
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
  - "exemplos [Visual Basic], arquivos de texto"
  - "Arquivos , gravando em"
  - "texto, escrevendo em arquivos"
  - "escrevendo em arquivos, em Meus Documentos"
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como gravar texto em arquivos no diret&#243;rio Meus Documentos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `My.Computer.FileSystem.SpecialDirectories` permite que você acesse pastas especiais, como o diretório **MyDocuments**.  
  
## Procedimento  
  
#### Para gravar novos arquivos de texto no diretório Meus Documentos  
  
1.  Use a propriedade `My.Computer.FileSystem.SpecialDirectories.MyDocuments` para fornecer o caminho.  
  
     [!CODE [VbFileIOWrite#1](../CodeSnippet/VS_Snippets_VBCSharp/VbFileIOWrite#1)]  
  
2.  Use o método `WriteAllText` para gravar texto para o arquivo especificado.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
## Exemplo  
 [!CODE [VbFileIOWrite#2](../CodeSnippet/VS_Snippets_VBCSharp/VbFileIOWrite#2)]  
  
## Compilando o código  
 Substitua `test.txt` pelo nome do arquivo você deseja para gravar.  
  
## Programação robusta  
 Este código joga todas as exceções que podem ocorrer ao gravar texto no arquivo.  Você pode reduzir a probabilidade de exceções usando controles Windows Forms como o [OpenFileDialog](../Topic/OpenFileDialog%20Component%20\(Windows%20Forms\).md) e o [SaveFileDialog](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md) que limitam as opções de usuário para nomes de arquivo válido.  Entretanto, usar esses controles é não à prova de falhas.  O sistema de arquivos pode alterar entre o momento que o usuário seleciona um arquivo e a hora que ele executa o código.  Manipulação de exceção é, portanto, quase sempre necessária quando se trabalha com arquivos.  
  
## Segurança do .NET Framework  
 Se você estiver executando em um contexto parcialmente confiável, o código pode lançar uma exceção devido a privilégios insuficientes.  Para obter mais informações, consulte [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md).  
  
 Este exemplo cria um novo arquivo.  Se um aplicativo precisa criar um arquivo, esse aplicativo precisa criar permissão para a pasta.  Permissões são feitas com listas de controle de acesso.  Se o arquivo já existe, o aplicativo precisa somente escrever permissão, um privilégio menor.  Quando possível, é mais seguro criar o arquivo durante a implantação e conceder privilégios para um único arquivo somente leitura e não para conceder privilégios de criação para uma pasta.  Além disso, é mais seguro gravar dados em pastas de usuário que em pasta raiz ou em pasta **Program Files**.  Para obter mais informações, consulte [ACL Technology Overview](http://msdn.microsoft.com/pt-br/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## Consulte também  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>