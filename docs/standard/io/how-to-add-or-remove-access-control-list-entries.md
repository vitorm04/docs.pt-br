---
title: Como adicionar ou remover entradas da lista de controle de acesso
ms.date: 03/30/2017
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
ms.openlocfilehash: 24c428a80f18b35d0aa3119a3c5fa1a6dcb2130e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>Como adicionar ou remover entradas da lista de controle de acesso
Para adicionar ou remover entradas da ACL (lista de controle de acesso) para ou de um arquivo, o objeto <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> deve ser obtido do arquivo ou diretório, modificado e aplicado ao arquivo ou diretório.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>Para adicionar ou remover uma entrada ACL de um arquivo  
  
1.  Chame o método <xref:System.IO.File.GetAccessControl%2A> para obter um objeto <xref:System.Security.AccessControl.FileSecurity> que contém as entradas ACL atuais de um arquivo.  
  
2.  Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.FileSecurity> retornado da etapa 1.  
  
3.  Passe o objeto <xref:System.Security.AccessControl.FileSecurity> para o método <xref:System.IO.File.SetAccessControl%2A> para aplicar as alterações.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>Para adicionar ou remover uma entrada ACL de um diretório  
  
1.  Chame o método <xref:System.IO.Directory.GetAccessControl%2A> para obter um objeto <xref:System.Security.AccessControl.DirectorySecurity> que contém as entradas ACL atuais de um diretório.  
  
2.  Adicionar ou remover entradas de ACL do objeto <xref:System.Security.AccessControl.DirectorySecurity> retornado da etapa 1.  
  
3.  Passe o objeto <xref:System.Security.AccessControl.DirectorySecurity> para o método <xref:System.IO.Directory.SetAccessControl%2A> para aplicar as alterações.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Você deve fornecer uma conta de grupo ou de usuário válida para executar este exemplo. Este exemplo usa um objeto <xref:System.IO.File>; no entanto, o mesmo procedimento é usado para as classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> e <xref:System.IO.DirectoryInfo>.
