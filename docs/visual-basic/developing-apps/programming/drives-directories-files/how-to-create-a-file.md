---
title: 'Como: Criar um arquivo no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 397db70cc8f5977bd861e9e6d6df2f0c8f884db2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967003"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="16be3-102">Como: Criar um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16be3-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="16be3-103">Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="16be3-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16be3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16be3-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="16be3-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="16be3-105">Compiling the Code</span></span>  
 <span data-ttu-id="16be3-106">Use a variável `file` para gravar no arquivo.</span><span class="sxs-lookup"><span data-stu-id="16be3-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="16be3-107">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="16be3-107">Robust Programming</span></span>  
 <span data-ttu-id="16be3-108">Se o arquivo já existir, ele será substituído.</span><span class="sxs-lookup"><span data-stu-id="16be3-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="16be3-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="16be3-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="16be3-110">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="16be3-110">The path name is malformed.</span></span> <span data-ttu-id="16be3-111">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="16be3-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="16be3-112">O caminho é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="16be3-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="16be3-113">O nome do caminho é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="16be3-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="16be3-114">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="16be3-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="16be3-115">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="16be3-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="16be3-116">O caminho é apenas dois-pontos ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="16be3-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="16be3-117">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="16be3-117">.NET Framework Security</span></span>  
 <span data-ttu-id="16be3-118">Uma <xref:System.Security.SecurityException> pode ser gerada em ambientes de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="16be3-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="16be3-119">A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="16be3-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="16be3-120">Uma <xref:System.UnauthorizedAccessException> será gerada se o usuário não tiver permissão para criar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="16be3-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16be3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16be3-121">See also</span></span>
- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="16be3-122">Usando bibliotecas de código parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="16be3-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="16be3-123">Noções Básicas da Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="16be3-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
