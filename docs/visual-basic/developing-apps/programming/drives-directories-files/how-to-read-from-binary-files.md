---
title: 'Como: Ler de arquivos binários em Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 88c9952818f6cb94db7b2da7ad44aa0da0eb43d2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825047"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="88c52-102">Como: Ler de arquivos binários em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88c52-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="88c52-103">O objeto `My.Computer.FileSystem` fornece o método `ReadAllBytes` para ler arquivos binários.</span><span class="sxs-lookup"><span data-stu-id="88c52-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="88c52-104">Para ler em um arquivo binário</span><span class="sxs-lookup"><span data-stu-id="88c52-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="88c52-105">Use o método `ReadAllBytes`, que retorna o conteúdo de um arquivo como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="88c52-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="88c52-106">Este exemplo lê do arquivo `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="88c52-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
-   <span data-ttu-id="88c52-107">Para arquivos binários grandes, é possível usar o método <xref:System.IO.FileStream.Read%2A> do objeto <xref:System.IO.FileStream> para ler apenas uma quantidade especificada do arquivo por vez.</span><span class="sxs-lookup"><span data-stu-id="88c52-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="88c52-108">Assim, é possível limitar quanto do arquivo é carregado na memória para cada operação de leitura.</span><span class="sxs-lookup"><span data-stu-id="88c52-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="88c52-109">O exemplo de código a seguir copia um arquivo e permite que o chamador especifique quanto do arquivo é lido na memória por operação de leitura.</span><span class="sxs-lookup"><span data-stu-id="88c52-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="88c52-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="88c52-110">Robust Programming</span></span>  
 <span data-ttu-id="88c52-111">As seguintes condições podem causar o lançamento de uma exceção:</span><span class="sxs-lookup"><span data-stu-id="88c52-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="88c52-112">O caminho não é válido por um destes motivos: é uma cadeia de caracteres de comprimento zero, contém somente espaço em branco, contém caracteres inválidos ou é um caminho de dispositivo (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="88c52-113">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="88c52-114">O arquivo não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="88c52-115">O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="88c52-116">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="88c52-117">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="88c52-118">Não há memória suficiente para gravar a cadeia de caracteres no buffer (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="88c52-119">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="88c52-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="88c52-120">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="88c52-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="88c52-121">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="88c52-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="88c52-122">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88c52-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="88c52-123">O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.</span><span class="sxs-lookup"><span data-stu-id="88c52-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c52-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88c52-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="88c52-125">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="88c52-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="88c52-126">Como: Ler de arquivos de texto com vários formatos</span><span class="sxs-lookup"><span data-stu-id="88c52-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="88c52-127">Armazenando Dados e Lendo da Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="88c52-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
