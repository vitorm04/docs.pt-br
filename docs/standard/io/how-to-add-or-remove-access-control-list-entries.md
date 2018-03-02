---
title: Como adicionar ou remover entradas da lista de controle de acesso
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 988fd354caa5fcc716107087242ead113c9a9939
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a><span data-ttu-id="17c5e-102">Como adicionar ou remover entradas da lista de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="17c5e-102">How to: Add or Remove Access Control List Entries</span></span>
<span data-ttu-id="17c5e-103">Para adicionar ou remover entradas da ACL (lista de controle de acesso) para ou de um arquivo, o objeto <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> deve ser obtido do arquivo ou diretório, modificado e aplicado ao arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="17c5e-103">To add or remove Access Control List (ACL) entries to or from a file, the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object must be obtained from the file or directory, modified, and then applied back to the file or directory.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="17c5e-104">Para adicionar ou remover uma entrada ACL de um arquivo</span><span class="sxs-lookup"><span data-stu-id="17c5e-104">To add or remove an ACL entry from a File</span></span>  
  
1.  <span data-ttu-id="17c5e-105">Chame o método <xref:System.IO.File.GetAccessControl%2A> para obter um objeto <xref:System.Security.AccessControl.FileSecurity> que contém as entradas ACL atuais de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="17c5e-105">Call the <xref:System.IO.File.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="17c5e-106">Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.FileSecurity> retornado da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="17c5e-106">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="17c5e-107">Passe o objeto <xref:System.Security.AccessControl.FileSecurity> para o método <xref:System.IO.File.SetAccessControl%2A> para aplicar as alterações.</span><span class="sxs-lookup"><span data-stu-id="17c5e-107">Pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A> method to apply the changes.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="17c5e-108">Para adicionar ou remover uma entrada ACL de um diretório</span><span class="sxs-lookup"><span data-stu-id="17c5e-108">To add or remove an ACL entry from a Directory</span></span>  
  
1.  <span data-ttu-id="17c5e-109">Chame o método <xref:System.IO.Directory.GetAccessControl%2A> para obter um objeto <xref:System.Security.AccessControl.DirectorySecurity> que contém as entradas ACL atuais de um diretório.</span><span class="sxs-lookup"><span data-stu-id="17c5e-109">Call the <xref:System.IO.Directory.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="17c5e-110">Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.DirectorySecurity> retornado da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="17c5e-110">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="17c5e-111">Passe o objeto <xref:System.Security.AccessControl.DirectorySecurity> para o método <xref:System.IO.Directory.SetAccessControl%2A> para aplicar as alterações.</span><span class="sxs-lookup"><span data-stu-id="17c5e-111">Pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A> method to apply the changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17c5e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17c5e-112">Example</span></span>  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17c5e-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="17c5e-113">Compiling the Code</span></span>  
 <span data-ttu-id="17c5e-114">Você deve fornecer uma conta de grupo ou de usuário válida para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="17c5e-114">You must supply a valid user or group account to run this example.</span></span> <span data-ttu-id="17c5e-115">Este exemplo usa um objeto <xref:System.IO.File>; no entanto, o mesmo procedimento é usado para as classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> e <xref:System.IO.DirectoryInfo>.</span><span class="sxs-lookup"><span data-stu-id="17c5e-115">This example uses a <xref:System.IO.File> object; however, the same procedure is used for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>
