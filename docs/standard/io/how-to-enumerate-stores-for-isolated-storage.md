---
title: "Como enumerar repositórios para o armazenamento isolado"
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
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Como enumerar repositórios para o armazenamento isolado
Você pode enumerar todos os armazenamentos isolados para o usuário atual usando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> método estático. Esse método usa um <xref:System.IO.IsolatedStorage.IsolatedStorageScope> valor e retorna um <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerador. Para enumerar repositórios, você deve ter o <xref:System.Security.Permissions.IsolatedStorageFilePermission> permissão que especifica o <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> valor. Se você chamar o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> método com o <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> valor, ele retorna uma matriz de <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objetos que são definidos para o usuário atual.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir obtém um armazenamento que é isolado por usuário e assembly, cria alguns arquivos e recupera os arquivos usando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> método.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
