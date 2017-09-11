---
title: Como criar um arquivo no Visual Basic
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
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
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
ms.openlocfilehash: d06d274b31afad0a437405d1679e0be7548f2e14
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="61ed6-102">Como criar um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61ed6-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="61ed6-103">Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="61ed6-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61ed6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61ed6-104">Example</span></span>  
 <span data-ttu-id="61ed6-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="61ed6-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61ed6-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="61ed6-106">Compiling the Code</span></span>  
 <span data-ttu-id="61ed6-107">Use a variável `file` para gravar no arquivo.</span><span class="sxs-lookup"><span data-stu-id="61ed6-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="61ed6-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="61ed6-108">Robust Programming</span></span>  
 <span data-ttu-id="61ed6-109">Se o arquivo já existir, ele será substituído.</span><span class="sxs-lookup"><span data-stu-id="61ed6-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="61ed6-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="61ed6-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="61ed6-111">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="61ed6-111">The path name is malformed.</span></span> <span data-ttu-id="61ed6-112">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="61ed6-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="61ed6-113">O caminho é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="61ed6-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="61ed6-114">O nome do caminho é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="61ed6-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="61ed6-115">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="61ed6-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="61ed6-116">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="61ed6-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="61ed6-117">O caminho é apenas dois-pontos ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="61ed6-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="61ed6-118">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61ed6-118">.NET Framework Security</span></span>  
 <span data-ttu-id="61ed6-119">Uma <xref:System.Security.SecurityException> pode ser gerada em ambientes de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="61ed6-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="61ed6-120">A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="61ed6-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="61ed6-121">Uma <xref:System.UnauthorizedAccessException> será gerada se o usuário não tiver permissão para criar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="61ed6-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ed6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61ed6-122">See Also</span></span>  
 <span data-ttu-id="61ed6-123"><xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="61ed6-123"><xref:System.IO></span></span>   
 <span data-ttu-id="61ed6-124"><xref:System.IO.File.Create%2A></span><span class="sxs-lookup"><span data-stu-id="61ed6-124"><xref:System.IO.File.Create%2A></span></span>   
 <span data-ttu-id="61ed6-125">[Usando Bibliotecas de Código Parcialmente Confiável](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span><span class="sxs-lookup"><span data-stu-id="61ed6-125">[Using Libraries from Partially Trusted Code](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span></span>  
 [<span data-ttu-id="61ed6-126">Noções Básicas da Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="61ed6-126">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

