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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="5e3ea-102">Como enumerar repositórios para o armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="5e3ea-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="5e3ea-103">Você pode enumerar todos os armazenamentos isolados para o usuário atual usando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> método estático.</span><span class="sxs-lookup"><span data-stu-id="5e3ea-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="5e3ea-104">Esse método usa um <xref:System.IO.IsolatedStorage.IsolatedStorageScope> valor e retorna um <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerador.</span><span class="sxs-lookup"><span data-stu-id="5e3ea-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="5e3ea-105">Para enumerar repositórios, você deve ter o <xref:System.Security.Permissions.IsolatedStorageFilePermission> permissão que especifica o <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> valor.</span><span class="sxs-lookup"><span data-stu-id="5e3ea-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="5e3ea-106">Se você chamar o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> método com o <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> valor, ele retorna uma matriz de <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objetos que são definidos para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="5e3ea-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e3ea-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e3ea-107">Example</span></span>  
 <span data-ttu-id="5e3ea-108">O exemplo de código a seguir obtém um armazenamento que é isolado por usuário e assembly, cria alguns arquivos e recupera os arquivos usando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5e3ea-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5e3ea-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e3ea-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="5e3ea-110">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="5e3ea-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
