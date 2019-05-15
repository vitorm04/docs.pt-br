---
title: 'Como: Ler texto de arquivos com um StreamReader (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 5631b402743a7be19428d15f55fbaa78b5b90668
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623348"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="def6c-102">Como: Ler texto de arquivos com um StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="def6c-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="def6c-103">O objeto `My.Computer.FileSystem` fornece métodos para abrir um <xref:System.IO.TextReader> e um <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="def6c-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="def6c-104">Esses métodos, `OpenTextFileWriter` e `OpenTextFileReader`, são métodos avançados que não aparecem no IntelliSense a menos que a guia **Todos** seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="def6c-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="def6c-105">Ler uma linha de um arquivo com um leitor de texto</span><span class="sxs-lookup"><span data-stu-id="def6c-105">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="def6c-106">Use o método `OpenTextFileReader` para abrir o <xref:System.IO.TextReader>, especificando o arquivo.</span><span class="sxs-lookup"><span data-stu-id="def6c-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="def6c-107">Esse exemplo abre o arquivo chamado `testfile.txt`, lê uma linha dele e exibe a linha em uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="def6c-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="def6c-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="def6c-108">Robust Programming</span></span>  
 <span data-ttu-id="def6c-109">O arquivo lido deve ser um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="def6c-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="def6c-110">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="def6c-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="def6c-111">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="def6c-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="def6c-112">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="def6c-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="def6c-113">O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.</span><span class="sxs-lookup"><span data-stu-id="def6c-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="def6c-114">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="def6c-114">.NET Framework Security</span></span>  
 <span data-ttu-id="def6c-115">Para ler de um arquivo, seu assembly requer um nível de privilégio concedido pela classe <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="def6c-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="def6c-116">Se você estiver executando em um contexto de confiança parcial, o código pode gerar uma exceção devido a privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="def6c-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="def6c-117">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="def6c-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="def6c-118">O usuário também precisa de acesso ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="def6c-118">The user also needs access to the file.</span></span> <span data-ttu-id="def6c-119">Para obter mais informações, consulte [Visão Geral da Tecnologia de ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="def6c-119">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def6c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="def6c-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="def6c-121">Componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="def6c-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [<span data-ttu-id="def6c-122">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="def6c-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
