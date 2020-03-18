---
title: 'Como: Adicionar ou remover entradas da Lista de Controle de Acesso (somente o Framework.NET)'
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
ms.openlocfilehash: 5f41c518b8732adff95593cab29d7085adcc9ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708122"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Como: Adicionar ou remover entradas da Lista de Controle de Acesso (somente o Framework.NET)
Para adicionar entradas ACL (lista de controle de acesso) a um arquivo ou um diretório ou removê-las de um arquivo ou um diretório, obtenha o objeto <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> no arquivo ou no diretório. Modifique o objeto e, em seguida, aplique-o novamente ao arquivo ou ao diretório.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Adicionar ou remover uma entrada ACL de um arquivo  
  
1. Chame o método <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> para obter um objeto <xref:System.Security.AccessControl.FileSecurity> que contém as entradas ACL atuais de um arquivo.  
  
2. Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.FileSecurity> retornado da etapa 1.  
  
3. Para aplicar as alterações, passe o objeto <xref:System.Security.AccessControl.FileSecurity> para o método <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Adicionar ou remover uma entrada ACL de um diretório  
  
1. Chame o método <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> para obter um objeto <xref:System.Security.AccessControl.DirectorySecurity> que contém as entradas ACL atuais de um diretório.  
  
2. Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.DirectorySecurity> retornado da etapa 1.  
  
3. Para aplicar as alterações, passe o objeto <xref:System.Security.AccessControl.DirectorySecurity> para o método <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
 Você precisará usar uma conta válida de grupo ou de usuário para executar este exemplo. O exemplo usa um objeto <xref:System.IO.File>. Use o mesmo procedimento para as classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> e <xref:System.IO.DirectoryInfo>.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
