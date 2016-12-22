---
title: "Como ler a partir de arquivos de texto separados por v&#237;rgulas no Visual Basic | Microsoft Docs"
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
  - "lendo arquivos de texto, delimitado por vírgula"
  - "arquivos de texto, lendo"
  - "arquivos de texto, tarefas"
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler a partir de arquivos de texto separados por v&#237;rgulas no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `TextFieldParser` fornece uma maneira para facilmente e com eficiência analisar arquivos texto estruturados, como logs.  A propriedade `TextFieldType` define se ele é um arquivo delimitado ou um arquivo com campos de texto de largura fixa .  
  
### Para analisar um arquivo de texto separado por vírgulas  
  
1.  Crie um novo `TextFieldParser`.  O código a seguir cria o `TextFieldParser` chamado `MyReader` e abre o arquivo `test.txt`.  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  Defina o tipo e delimitador do `TextField` .  O código a seguir define a propriedade `TextFieldType` como `Delimited` e o delimitador como ",".  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  Faça um loop através dos campos no arquivo.  Se alguma linha estiver corrompida, relate um erro e continue a análise.  O código a seguir faz um loop no arquivo, exibindo cada campo por vez e relatando quaisquer campos que estejam formatados incorretamente.  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  Feche os blocos `While` e `Using` com `End While` e `End Using`.  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## Exemplo  
 Este exemplo lê a partir do arquivo `test.txt`.  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Uma linha não pode ser analisado usando o formato especificado  \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\).  A mensagem de exceção Especifica a linha causando a exceção, enquanto o <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property é atribuída o texto contido na linha.  
  
-   O arquivo especificado não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   Uma situação de confiança parcial \(partial\-trust\) na qual o usuário não tem permissões suficientes para acessar o arquivo.  \(<xref:System.Security.SecurityException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [Como ler a partir de arquivos de texto de largura fixa](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Como ler a partir de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Solucionando problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Exceções de solução de problemas: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)