---
title: "Analisando arquivos de texto com o objeto TextFieldParser (Visual Basic) | Microsoft Docs"
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
  - "E/S [Visual Basic], analisando arquivos"
  - "Objeto TextFieldParser, usando"
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Analisando arquivos de texto com o objeto TextFieldParser (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `TextFieldParser` permite que você analise e processe arquivos muito grandes que são estruturados como colunas do texto de largura delimitada, como arquivos de log ou informações do banco de dados herdadas.  Analisar um arquivo de texto com `TextFieldParser` é semelhante a iterar em um arquivo texto, enquanto o método de análise para extrair campos de texto é semelhante aos métodos para manipulação de sequência de caracteres usados para transformar em símbolos sequências de caracteres.  
  
## Analisar Diferentes Tipos de Arquivos de Texto  
 Arquivos de Texto podem ter campos de várias larguras, delimitados por um caractere, como uma vírgula ou um espaço de tabulação.  Defina `TextFieldType` e o delimitador, como no exemplo a seguir, que usa o método `SetDelimiters` para definir um arquivo de texto delimitado por tabulações:  
  
 [!CODE [VbVbalrTextFieldParser#21](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTextFieldParser#21)]  
  
 Outros arquivos de texto podem ter larguras de campo que são fixas.  Em tais casos, você precisará definir o `TextFieldType` como `FixedWidth` e definir as larguras de cada campo, como no exemplo a seguir.  Este exemplo usa o método `SetFieldWidths` para definir as colunas de texto: a primeira coluna tem 5 caracteres de largura, a segunda tem 10, a terceira tem 11, e a quarta tem largura variável.  
  
 [!CODE [VbVbalrTextFieldParser#22](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTextFieldParser#22)]  
  
 Uma vez que o formato é definido, você pode executar um loop através do arquivo, usando o método `ReadFields` para processar cada linha em retorno.  
  
 Se um campo não coincidir com o formato especificado, será apresentada uma exceção <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>.  Quando essas exceções são lançadas, o `ErrorLine` e `ErrorLineNumber` propriedades mantém o texto causador da exceção e o número da linha do texto.  
  
## Analisar Arquivos com Vários Formatos  
 O método `PeekChars` do objeto `TextFieldParser` pode ser usado para verificar cada campo antes da leitura, permitindo\-lhe definir vários formatos para os campos e reagir adequadamente.  Para obter mais informações, consulte [Como ler a partir de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>   
 [Exceções de solução de problemas: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)