---
title: "Como ler a partir de arquivos de texto com v&#225;rios formatos no Visual Basic | Microsoft Docs"
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
  - "E/S [Visual Basic], lendo arquivos de texto"
  - "Método My.Computer.FileSystem.WriteAllText, analisando arquivos de texto estruturado"
  - "Método PeekChars, determinando o formato do texto"
  - "lendo arquivos de texto, vários formatos"
  - "arquivos de texto, lendo"
  - "Objeto TextFieldParser, lendo de um arquivo"
  - "Enumeração TextFieldType"
  - "Método WriteAllText, analisando arquivos de texto estruturado"
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler a partir de arquivos de texto com v&#225;rios formatos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> fornece uma maneira para facilmente e com eficiência analisar arquivos texto estruturados, como logs.  Você pode processar um arquivo com vários formatos usando o método `PeekChars` para determinar o formato de cada linha conforme você analisa através do arquivo.  
  
### Para analisar um arquivo de texto com vários formatos  
  
1.  Adicione um arquivo de texto chamado Testfile. txt ao seu projeto.  Adicione o seguinte conteúdo para o arquivo de texto.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  Defina o formato esperado e o formato usado quando um erro é relatado.  A última entrada em cada matriz é \-1, portanto o último campo será considerado de largura variável.  Isso ocorre quando a última entrada na matriz é menor ou igual a 0.  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  Criar uma nova <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> o objeto, definindo a largura e o formato.  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  Percorra as linhas, testando seus formatos antes da leitura.  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  Grave erros no console.  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## Exemplo  
 Veja a seguir o exemplo completo que lê a partir do arquivo `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Uma linha não pode ser analisado usando o formato especificado  \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\).  A mensagem de exceção Especifica a linha causando a exceção, enquanto o <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property é atribuída ao texto contido na linha.  
  
-   O arquivo especificado não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   Uma situação de confiança parcial \(partial\-trust\) na qual o usuário não tem permissões suficientes para acessar o arquivo.  \(<xref:System.Security.SecurityException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 [Como ler a partir de arquivos de texto separados por vírgulas](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [Como ler a partir de arquivos de texto de largura fixa](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)