---
title: Como gravar texto em arquivos no diretório Meus Documentos no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 894458ad6d69b8bb2836518b90723703733208b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264513"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="a1fff-102">Como gravar texto em arquivos no diretório Meus Documentos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1fff-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="a1fff-103">O objeto `My.Computer.FileSystem.SpecialDirectories` permite que você acesse diretórios especiais, como o diretório **MyDocuments**.</span><span class="sxs-lookup"><span data-stu-id="a1fff-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a1fff-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="a1fff-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="a1fff-105">Para gravar novos arquivos de texto no diretório Meus Documentos</span><span class="sxs-lookup"><span data-stu-id="a1fff-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="a1fff-106">Use a propriedade `My.Computer.FileSystem.SpecialDirectories.MyDocuments` para fornecer o caminho.</span><span class="sxs-lookup"><span data-stu-id="a1fff-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="a1fff-107">Use o método `WriteAllText` para escrever o texto no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="a1fff-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a1fff-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1fff-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1fff-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a1fff-109">Compiling the Code</span></span>  
 <span data-ttu-id="a1fff-110">Substitua `test.txt` pelo nome do arquivo no qual você deseja gravar.</span><span class="sxs-lookup"><span data-stu-id="a1fff-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a1fff-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a1fff-111">Robust Programming</span></span>  
 <span data-ttu-id="a1fff-112">Esse código lança novamente todas as exceções que podem ocorrer ao gravar texto no arquivo.</span><span class="sxs-lookup"><span data-stu-id="a1fff-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="a1fff-113">É possível reduzir a probabilidade de exceções usando controles do Windows Forms como os componentes [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) que limitam as escolhas do usuário para validar nomes de arquivo.</span><span class="sxs-lookup"><span data-stu-id="a1fff-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="a1fff-114">No entanto, o uso desses controles não é à prova de falhas.</span><span class="sxs-lookup"><span data-stu-id="a1fff-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="a1fff-115">O sistema de arquivos pode ser alterado entre o momento em que o usuário seleciona um arquivo e o momento em que o código é executado.</span><span class="sxs-lookup"><span data-stu-id="a1fff-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="a1fff-116">Portanto, o tratamento de exceções é quase sempre é necessário ao trabalhar com arquivos.</span><span class="sxs-lookup"><span data-stu-id="a1fff-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a1fff-117">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a1fff-117">.NET Framework Security</span></span>  
 <span data-ttu-id="a1fff-118">Se você estiver executando em um contexto de confiança parcial, o código pode gerar uma exceção devido a privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="a1fff-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="a1fff-119">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="a1fff-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="a1fff-120">Esse exemplo cria um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="a1fff-120">This example creates a new file.</span></span> <span data-ttu-id="a1fff-121">Se um aplicativo precisar criar um arquivo, esse aplicativo precisará da permissão de criação para a pasta.</span><span class="sxs-lookup"><span data-stu-id="a1fff-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="a1fff-122">As permissões são definidas usando listas de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="a1fff-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="a1fff-123">Se o arquivo já existir, o aplicativo precisará somente da permissão de gravação, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="a1fff-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="a1fff-124">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder privilégios de leitura para um único arquivo, em vez de conceder privilégios de criação para uma pasta.</span><span class="sxs-lookup"><span data-stu-id="a1fff-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="a1fff-125">Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta **Arquivos de Programas**.</span><span class="sxs-lookup"><span data-stu-id="a1fff-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="a1fff-126">Para obter mais informações, consulte [Visão Geral da Tecnologia de ACL](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="a1fff-126">For more information, see [ACL Technology Overview](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fff-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1fff-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
