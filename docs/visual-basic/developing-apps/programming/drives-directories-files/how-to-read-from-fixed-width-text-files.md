---
title: "Como ler a partir de arquivos de texto de largura fixa no Visual Basic | Microsoft Docs"
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
  - "Arquivos , analisando"
  - "arquivo de texto de largura fixa"
  - "lendo arquivos de texto, largura fixa"
  - "arquivos de texto, lendo"
  - "arquivos de texto, tarefas"
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler a partir de arquivos de texto de largura fixa no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `TextFieldParser` fornece uma maneira para facilmente e com eficiência analisar arquivos texto estruturados, como logs.  
  
 O `TextFieldType` propriedade define se o arquivo analisado é um arquivo delimitado ou que possui campos de texto de largura fixa.  Em um arquivo de texto de largura fixa, o campo no final pode ter uma largura variável.  Para especificar o campo no final tem uma largura variável, defina\-o para ter uma largura menor que ou igual a zero.  
  
### Para analisar um arquivo de texto de largura fixa  
  
1.  Crie um novo `TextFieldParser`.  O código a seguir cria o `TextFieldParser` chamado `Reader` e abre o arquivo `test.log`.  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  Defina a propriedade `TextFieldType` como `FixedWidth`, definindo a largura e o formato.  O código a seguir define as colunas de texto; a primeira tem 5 caracteres de largura, a segunda tem 10 , a terceira tem  11, e a quarta é de largura variável..  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  Faça um loop através dos campos no arquivo.  Se alguma das linhas estiver corrompida, relate um erro e continue analisando.  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  Feche os blocos `While` e `Using` com `End While` e `End Using`.  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## Exemplo  
 Este exemplo lê a partir do arquivo `test.log`.  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Uma linha não pode ser analisado usando o formato especificado  \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\).  A mensagem de exceção Especifica a linha causando a exceção, enquanto o <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property é atribuída ao texto contido na linha.  
  
-   O arquivo especificado não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   Uma situação de confiança parcial \(partial\-trust\) na qual o usuário não tem permissões suficientes para acessar o arquivo.  \(<xref:System.Security.SecurityException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [Como ler a partir de arquivos de texto separados por vírgulas](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [Como ler a partir de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Solucionando problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Exceções de solução de problemas: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)