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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 16038ffbe090cfd8d2c0578f75e66db3b021cb9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>Como adicionar ou remover entradas da lista de controle de acesso
Para adicionar ou remover entradas da lista de controle de acesso (ACL) para ou de um arquivo, o <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> objeto deve ser obtido do arquivo ou diretório, modificado e, em seguida, é aplicado para o arquivo ou diretório.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>Para adicionar ou remover uma entrada ACL de um arquivo  
  
1.  Chamar o <xref:System.IO.File.GetAccessControl%2A> método para obter um <xref:System.Security.AccessControl.FileSecurity> objeto que contém as entradas ACL atuais de um arquivo.  
  
2.  Adicionar ou remover entradas de ACL do <xref:System.Security.AccessControl.FileSecurity> objeto retornado da etapa 1.  
  
3.  Passar o <xref:System.Security.AccessControl.FileSecurity> o objeto para o <xref:System.IO.File.SetAccessControl%2A> método para aplicar as alterações.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>Para adicionar ou remover uma entrada ACL de um diretório  
  
1.  Chamar o <xref:System.IO.Directory.GetAccessControl%2A> método para obter um <xref:System.Security.AccessControl.DirectorySecurity> objeto que contém as entradas ACL atuais de um diretório.  
  
2.  Adicionar ou remover entradas de ACL do <xref:System.Security.AccessControl.DirectorySecurity> objeto retornado da etapa 1.  
  
3.  Passar o <xref:System.Security.AccessControl.DirectorySecurity> o objeto para o <xref:System.IO.Directory.SetAccessControl%2A> método para aplicar as alterações.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Você deve fornecer uma conta de grupo ou de usuário válido para executar este exemplo. Este exemplo usa um <xref:System.IO.File> objeto; no entanto, o mesmo procedimento é usado para o <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, e <xref:System.IO.DirectoryInfo> classes.
