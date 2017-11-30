---
title: Como criar um arquivo no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="f11f5-102">Como criar um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f11f5-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="f11f5-103">Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="f11f5-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f11f5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f11f5-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f11f5-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f11f5-105">Compiling the Code</span></span>  
 <span data-ttu-id="f11f5-106">Use a variável `file` para gravar no arquivo.</span><span class="sxs-lookup"><span data-stu-id="f11f5-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f11f5-107">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="f11f5-107">Robust Programming</span></span>  
 <span data-ttu-id="f11f5-108">Se o arquivo já existir, ele será substituído.</span><span class="sxs-lookup"><span data-stu-id="f11f5-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="f11f5-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="f11f5-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f11f5-110">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="f11f5-110">The path name is malformed.</span></span> <span data-ttu-id="f11f5-111">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f11f5-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f11f5-112">O caminho é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f11f5-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f11f5-113">O nome do caminho é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f11f5-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f11f5-114">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f11f5-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f11f5-115">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f11f5-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f11f5-116">O caminho é apenas dois-pontos ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f11f5-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f11f5-117">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f11f5-117">.NET Framework Security</span></span>  
 <span data-ttu-id="f11f5-118">Uma <xref:System.Security.SecurityException> pode ser gerada em ambientes de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="f11f5-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="f11f5-119">A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="f11f5-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="f11f5-120">Uma <xref:System.UnauthorizedAccessException> será gerada se o usuário não tiver permissão para criar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f11f5-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11f5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f11f5-121">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [<span data-ttu-id="f11f5-122">Usando bibliotecas de código parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="f11f5-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [<span data-ttu-id="f11f5-123">Noções Básicas da Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="f11f5-123">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)
