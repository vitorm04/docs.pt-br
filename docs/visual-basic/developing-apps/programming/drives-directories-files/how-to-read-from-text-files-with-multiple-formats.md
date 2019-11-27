---
title: 'Como: ler de arquivos de texto com vários formatos'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334579"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="fbebf-102">Como: ler de arquivos FEXT com vários formatos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbebf-102">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="fbebf-103">O objeto <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> fornece uma maneira fácil e eficiente de analisar arquivos de texto estruturados, como logs.</span><span class="sxs-lookup"><span data-stu-id="fbebf-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="fbebf-104">É possível processar um arquivo com vários formatos usando o método `PeekChars` para determinar o formato de cada linha conforme você analisa por meio do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fbebf-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="fbebf-105">Para analisar um arquivo de texto com vários formatos</span><span class="sxs-lookup"><span data-stu-id="fbebf-105">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="fbebf-106">Adicione um arquivo de texto chamado *Testfile. txt* ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="fbebf-106">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="fbebf-107">Adicione o seguinte conteúdo ao arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="fbebf-107">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="fbebf-108">Defina o formato esperado e o formato usado quando um erro é relatado.</span><span class="sxs-lookup"><span data-stu-id="fbebf-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="fbebf-109">A última entrada em cada matriz é -1, portanto, supõe-se que o último campo tenha largura variável.</span><span class="sxs-lookup"><span data-stu-id="fbebf-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="fbebf-110">Isso ocorre quando a última entrada na matriz é menor ou igual a 0.</span><span class="sxs-lookup"><span data-stu-id="fbebf-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="fbebf-111">Crie um novo objeto <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>, definindo a largura e o formato.</span><span class="sxs-lookup"><span data-stu-id="fbebf-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="fbebf-112">Percorra as linhas, testando seus formatos antes da leitura.</span><span class="sxs-lookup"><span data-stu-id="fbebf-112">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="fbebf-113">Grave os erros no console.</span><span class="sxs-lookup"><span data-stu-id="fbebf-113">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="fbebf-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fbebf-114">Example</span></span>

<span data-ttu-id="fbebf-115">Veja a seguir o exemplo completo que lê a partir do arquivo `testfile.txt`:</span><span class="sxs-lookup"><span data-stu-id="fbebf-115">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="fbebf-116">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fbebf-116">Robust programming</span></span>

<span data-ttu-id="fbebf-117">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="fbebf-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="fbebf-118">Não é possível analisar uma linha usando o formato especificado (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="fbebf-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="fbebf-119">A mensagem de exceção especifica a linha que está causando a exceção, enquanto a propriedade <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> é atribuída ao texto contido na linha.</span><span class="sxs-lookup"><span data-stu-id="fbebf-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="fbebf-120">O arquivo especificado não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="fbebf-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="fbebf-121">Uma situação de confiança parcial na qual o usuário não tem permissões suficientes para acessar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="fbebf-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="fbebf-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fbebf-122">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="fbebf-123">O caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="fbebf-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="fbebf-124">O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="fbebf-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbebf-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbebf-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="fbebf-126">Como ler a partir de arquivos de texto separados por vírgulas</span><span class="sxs-lookup"><span data-stu-id="fbebf-126">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="fbebf-127">Como ler a partir de arquivos de texto de largura fixa</span><span class="sxs-lookup"><span data-stu-id="fbebf-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="fbebf-128">Analisando arquivos de texto com o objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="fbebf-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
