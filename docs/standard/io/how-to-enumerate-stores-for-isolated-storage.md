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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c4fa63c5c7f966831a55c9103c9ba58cfa621d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Como enumerar repositórios para o armazenamento isolado
Você pode enumerar todos os repositórios isolados para o usuário atual usando o método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>. Esse método usa um valor <xref:System.IO.IsolatedStorage.IsolatedStorageScope> e retorna um enumerador <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Para enumerar os repositórios, você deve ter a permissão <xref:System.Security.Permissions.IsolatedStorageFilePermission> que especifica o valor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>. Se você chamar o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> com o valor <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, ele retornará uma matriz de objetos <xref:System.IO.IsolatedStorage.IsolatedStorageFile> que são definidos para o usuário atual.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir obtém um repositório que é isolado pelo usuário e pelo assembly, cria alguns arquivos e recupera esses arquivos usando o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
