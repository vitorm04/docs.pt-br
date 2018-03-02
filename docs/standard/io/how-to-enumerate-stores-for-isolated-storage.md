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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="d9bca-102">Como enumerar repositórios para o armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="d9bca-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="d9bca-103">Você pode enumerar todos os repositórios isolados para o usuário atual usando o método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9bca-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="d9bca-104">Esse método usa um valor <xref:System.IO.IsolatedStorage.IsolatedStorageScope> e retorna um enumerador <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.</span><span class="sxs-lookup"><span data-stu-id="d9bca-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="d9bca-105">Para enumerar os repositórios, você deve ter a permissão <xref:System.Security.Permissions.IsolatedStorageFilePermission> que especifica o valor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="d9bca-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="d9bca-106">Se você chamar o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> com o valor <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, ele retornará uma matriz de objetos <xref:System.IO.IsolatedStorage.IsolatedStorageFile> que são definidos para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="d9bca-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9bca-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9bca-107">Example</span></span>  
 <span data-ttu-id="d9bca-108">O exemplo de código a seguir obtém um repositório que é isolado pelo usuário e pelo assembly, cria alguns arquivos e recupera esses arquivos usando o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9bca-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d9bca-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9bca-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="d9bca-110">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="d9bca-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
