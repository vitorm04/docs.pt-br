---
title: "Como ler em arquivos de texto separados por vírgulas no Visual Basic | Microsoft Docs"
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
- files, parsing
- text files, tasks
- reading text files, comma-delimited
- text files, reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: 19
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f894aa1dce23d5c8da7287275123349739152f04
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Como ler em arquivos de texto separados por vírgulas no Visual Basic
O objeto `TextFieldParser` fornece uma maneira fácil e eficiente de analisar arquivos de texto estruturados, como logs. A propriedade `TextFieldType` define se ele é um arquivo delimitado ou um arquivo com campos de texto de largura fixa.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Para analisar um arquivo de texto delimitado por vírgulas  
  
1.  Crie um novo `TextFieldParser`. O código a seguir cria o `TextFieldParser` chamado `MyReader` e abre o arquivo `test.txt`.  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  Defina o delimitador e o tipo `TextField`. O código a seguir define a propriedade `TextFieldType` como `Delimited` e o delimitador como “,”.  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  Percorra em loop os campos no arquivo. Se alguma linha estiver corrompida, relate um erro e continue a análise. O código a seguir faz um loop pelo arquivo, exibindo cada campo por sua vez e relatando quaisquer campos que estejam formatados incorretamente.  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  Feche os blocos `While` e `Using` com `End While` e `End Using`.  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo lê do arquivo `test.txt`.  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Não foi possível analisar uma linha usando o formato especificado (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). A mensagem de exceção especifica a linha que causou a exceção, enquanto a propriedade <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> é atribuída ao texto contido na linha.  
  
-   O arquivo especificado não existe (<xref:System.IO.FileNotFoundException>).  
  
-   Uma situação de confiança parcial na qual o usuário não tem permissões suficientes para acessar o arquivo. (<xref:System.Security.SecurityException>).  
  
-   O caminho é muito longo (<xref:System.IO.PathTooLongException>).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [Como ler em arquivos de texto de largura fixa](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Como ler em arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Passo a passo: manipulando arquivos e diretórios no Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Solução de problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
