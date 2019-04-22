---
title: 'Como: Gravar texto em arquivos no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f4d6c3ef5ba6d8aa286e1ae2bd8a944aacdad096
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828219"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="ee4a1-102">Como: Gravar texto em arquivos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee4a1-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="ee4a1-103">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pode ser usado para gravar texto em arquivos.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="ee4a1-104">Se o arquivo especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ee4a1-105">Procedimento</span><span class="sxs-lookup"><span data-stu-id="ee4a1-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="ee4a1-106">Para gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="ee4a1-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="ee4a1-107">Use o método `WriteAllText` para gravar texto em um arquivo, especificando o arquivo e o texto a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="ee4a1-108">Este exemplo grava a linha `"This is new text."` no arquivo chamado `test.txt`, anexando o texto a qualquer texto existente no arquivo.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="ee4a1-109">Para gravar uma série de cadeias de caracteres em um arquivo</span><span class="sxs-lookup"><span data-stu-id="ee4a1-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="ee4a1-110">Faça um loop na coleção de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-110">Loop through the string collection.</span></span> <span data-ttu-id="ee4a1-111">Use o método `WriteAllText` para gravar texto em um arquivo, especificando o arquivo de destino e a cadeia de caracteres a ser adicionada e configurando `append` como `True`.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="ee4a1-112">Este exemplo grava os nomes dos arquivos no diretório `Documents and Settings` em `FileList.txt`, inserindo um retorno de carro entre cada um para obter melhor legibilidade.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ee4a1-113">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="ee4a1-113">Robust Programming</span></span>  
 <span data-ttu-id="ee4a1-114">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="ee4a1-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ee4a1-115">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-116">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-117">`File` aponta para um caminho que não existe (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-118">O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-119">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-120">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-121">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="ee4a1-122">O disco está cheio e a chamada a `WriteAllText` falha (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="ee4a1-123">Se você estiver executando em um contexto de confiança parcial, o código pode gerar uma exceção devido a privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="ee4a1-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ee4a1-124">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ee4a1-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4a1-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee4a1-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="ee4a1-126">Como: Ler de arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="ee4a1-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
