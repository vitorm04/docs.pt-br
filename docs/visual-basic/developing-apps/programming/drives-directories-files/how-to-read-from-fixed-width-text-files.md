---
title: 'Como: ler de arquivos de texto de largura fixa'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 77b2e0a4ebe36b68501f821ef5731935ee3b16a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411623"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="69a83-102">Como ler de arquivos de texto de largura fixa no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69a83-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="69a83-103">O objeto `TextFieldParser` fornece uma maneira fácil e eficiente de analisar arquivos de texto estruturados, como logs.</span><span class="sxs-lookup"><span data-stu-id="69a83-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="69a83-104">A propriedade `TextFieldType` define se o arquivo analisado é um arquivo delimitado ou um arquivo com campos de texto de largura fixa.</span><span class="sxs-lookup"><span data-stu-id="69a83-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="69a83-105">Em um arquivo de texto de largura fixa, o campo no final pode ter largura variável.</span><span class="sxs-lookup"><span data-stu-id="69a83-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="69a83-106">Para especificar que o campo no final tenha largura variável, defina sua largura como menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="69a83-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="69a83-107">Para analisar um arquivo de texto de largura fixa</span><span class="sxs-lookup"><span data-stu-id="69a83-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="69a83-108">Crie um `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="69a83-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="69a83-109">O código a seguir cria o `TextFieldParser` chamado `Reader` e abre o arquivo `test.log`.</span><span class="sxs-lookup"><span data-stu-id="69a83-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="69a83-110">Defina a propriedade `TextFieldType` como `FixedWidth`, definindo a largura e o formato.</span><span class="sxs-lookup"><span data-stu-id="69a83-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="69a83-111">O código a seguir define as colunas de texto; a primeira tem 5 caracteres de largura, a segunda tem 10, a terceira tem 11 e a quarta tem largura variável.</span><span class="sxs-lookup"><span data-stu-id="69a83-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="69a83-112">Percorra em loop os campos no arquivo.</span><span class="sxs-lookup"><span data-stu-id="69a83-112">Loop through the fields in the file.</span></span> <span data-ttu-id="69a83-113">Se alguma linha estiver corrompida, relate um erro e continue com a análise.</span><span class="sxs-lookup"><span data-stu-id="69a83-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="69a83-114">Feche os blocos `While` e `Using` com `End While` e `End Using`.</span><span class="sxs-lookup"><span data-stu-id="69a83-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="69a83-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69a83-115">Example</span></span>  

 <span data-ttu-id="69a83-116">Este exemplo lê do arquivo `test.log`.</span><span class="sxs-lookup"><span data-stu-id="69a83-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="69a83-117">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="69a83-117">Robust programming</span></span>  

 <span data-ttu-id="69a83-118">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="69a83-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="69a83-119">Não é possível analisar uma linha usando o formato especificado (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="69a83-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="69a83-120">A mensagem de exceção especifica a linha que está causando a exceção, enquanto a propriedade <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> é atribuída ao texto contido na linha.</span><span class="sxs-lookup"><span data-stu-id="69a83-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="69a83-121">O arquivo especificado não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="69a83-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="69a83-122">Uma situação de confiança parcial na qual o usuário não tem permissões suficientes para acessar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="69a83-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="69a83-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="69a83-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="69a83-124">O caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="69a83-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="69a83-125">O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="69a83-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a83-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="69a83-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="69a83-127">Como: ler de arquivos de texto separados por vírgula</span><span class="sxs-lookup"><span data-stu-id="69a83-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="69a83-128">Como: ler de arquivos de texto com vários formatos</span><span class="sxs-lookup"><span data-stu-id="69a83-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="69a83-129">Analisando arquivos de texto com o objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="69a83-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="69a83-130">Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69a83-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="69a83-131">Solução de problemas: ler e gravar em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="69a83-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
