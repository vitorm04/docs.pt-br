---
title: 'Como: Adicionar ou remover entradas da lista de controle de acesso (somente .NET Framework)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 351d8325cc0fc1a1b551b6d513cad02f1291daab
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308010"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="19e2c-102">Como: Adicionar ou remover entradas da lista de controle de acesso (somente .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="19e2c-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="19e2c-103">Para adicionar entradas ACL (lista de controle de acesso) a um arquivo ou um diretório ou removê-las de um arquivo ou um diretório, obtenha o objeto <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> no arquivo ou no diretório.</span><span class="sxs-lookup"><span data-stu-id="19e2c-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="19e2c-104">Modifique o objeto e, em seguida, aplique-o novamente ao arquivo ou ao diretório.</span><span class="sxs-lookup"><span data-stu-id="19e2c-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="19e2c-105">Adicionar ou remover uma entrada ACL de um arquivo</span><span class="sxs-lookup"><span data-stu-id="19e2c-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="19e2c-106">Chame o método <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> para obter um objeto <xref:System.Security.AccessControl.FileSecurity> que contém as entradas ACL atuais de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="19e2c-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="19e2c-107">Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.FileSecurity> retornado da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="19e2c-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="19e2c-108">Para aplicar as alterações, passe o objeto <xref:System.Security.AccessControl.FileSecurity> para o método <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19e2c-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="19e2c-109">Adicionar ou remover uma entrada ACL de um diretório</span><span class="sxs-lookup"><span data-stu-id="19e2c-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="19e2c-110">Chame o método <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> para obter um objeto <xref:System.Security.AccessControl.DirectorySecurity> que contém as entradas ACL atuais de um diretório.</span><span class="sxs-lookup"><span data-stu-id="19e2c-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="19e2c-111">Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.DirectorySecurity> retornado da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="19e2c-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="19e2c-112">Para aplicar as alterações, passe o objeto <xref:System.Security.AccessControl.DirectorySecurity> para o método <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19e2c-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19e2c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19e2c-113">Example</span></span>  
 <span data-ttu-id="19e2c-114">Você precisará usar uma conta válida de grupo ou de usuário para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="19e2c-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="19e2c-115">O exemplo usa um objeto <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="19e2c-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="19e2c-116">Use o mesmo procedimento para as classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> e <xref:System.IO.DirectoryInfo>.</span><span class="sxs-lookup"><span data-stu-id="19e2c-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
