---
title: Analisando arquivos de texto com o objeto TextFieldParser (Visual Basic)
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
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files, parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: 20
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ad7407ca1928f9b4a2405bc5831777fbf965b61f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="d8254-102">Analisando arquivos de texto com o objeto TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8254-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="d8254-103">O objeto `TextFieldParser` permite analisar e processar arquivos muito grandes estruturados como colunas de texto de largura delimitada, como arquivos de log ou informações de banco de dados herdadas.</span><span class="sxs-lookup"><span data-stu-id="d8254-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="d8254-104">Analisar um arquivo de texto com `TextFieldParser` é semelhante a iterar em um arquivo de texto, enquanto o método de análise para extrair campos de texto é semelhante a métodos de manipulação de cadeias de caracteres usados para criar tokens para cadeias de caracteres delimitadas.</span><span class="sxs-lookup"><span data-stu-id="d8254-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="d8254-105">Analisando tipos diferentes de arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="d8254-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="d8254-106">Arquivos de texto podem ter campos com larguras variadas, delimitados por um caractere como uma vírgula ou um espaço de tabulação.</span><span class="sxs-lookup"><span data-stu-id="d8254-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="d8254-107">Defina `TextFieldType` e o delimitador, como no exemplo a seguir, que usa o método `SetDelimiters` para definir um arquivo de texto delimitado por tabulação:</span><span class="sxs-lookup"><span data-stu-id="d8254-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 <span data-ttu-id="d8254-108">[!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8254-108">[!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]</span></span>  
  
 <span data-ttu-id="d8254-109">Outros arquivos de texto podem ter larguras de campo fixas.</span><span class="sxs-lookup"><span data-stu-id="d8254-109">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="d8254-110">Nesses casos, você precisa definir o `TextFieldType` como `FixedWidth` e definir as larguras de cada campo, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8254-110">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="d8254-111">Este exemplo usa o método `SetFieldWidths` para definir as colunas de texto: a primeira coluna tem 5 caracteres de largura, a segunda tem 10, a terceira tem 11 e a quarta tem largura variável.</span><span class="sxs-lookup"><span data-stu-id="d8254-111">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 <span data-ttu-id="d8254-112">[!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8254-112">[!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]</span></span>  
  
 <span data-ttu-id="d8254-113">Após o formato ser definido, você pode executar um loop no arquivo, usando o método `ReadFields` para processar uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="d8254-113">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="d8254-114">Se um campo não coincidir com o formato especificado, uma exceção <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="d8254-114">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="d8254-115">Quando essas exceções são geradas, as propriedades `ErrorLine` e `ErrorLineNumber` retêm o texto causador da exceção e o número de linha do texto.</span><span class="sxs-lookup"><span data-stu-id="d8254-115">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="d8254-116">Analisando arquivos com vários formatos</span><span class="sxs-lookup"><span data-stu-id="d8254-116">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="d8254-117">O método `PeekChars` do objeto `TextFieldParser` pode ser usado para verificar cada campo antes da leitura, permitindo definir vários formatos para os campos e reagir adequadamente.</span><span class="sxs-lookup"><span data-stu-id="d8254-117">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="d8254-118">Para obter mais informações, consulte [Como ler de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="d8254-118">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8254-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8254-119">See also</span></span>  
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

