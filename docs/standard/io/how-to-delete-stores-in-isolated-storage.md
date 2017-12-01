---
title: "Como excluir repositórios no armazenamento isolado"
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
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 138d1688f22cdc3bfa542af5433b6dbf8139e840
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Como excluir repositórios no armazenamento isolado
O <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe fornece dois métodos para excluir os arquivos de armazenamento isolado:  
  
-   O método de instância <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> não tem nenhum argumento e exclui o armazenamento que o chama. Nenhuma permissão é necessária para esta operação. Qualquer código que pode acessar o armazenamento pode excluir qualquer ou todos os dados dentro dele.  
  
-   O método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> leva o <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> valor de enumeração e exclui todos os armazenamentos para o usuário que está executando o código. Esta operação requer <xref:System.Security.Permissions.IsolatedStorageFilePermission> permissão para o <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> valor.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra o uso de estático e a instância <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> métodos. A classe obtém dois repositórios; uma é isolada para usuário e o assembly e a outra é isolada para usuário, domínio e assembly. O armazenamento de usuário, domínio e assembly é excluído chamando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> método do arquivo de armazenamento isolado `isoStore1`. Em seguida, todos os armazenamentos restantes para o usuário são excluídos chamando o método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
