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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ae04deeb8d23b496a9111b0d4b5b68e12ac1439
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="23b1d-102">Como excluir repositórios no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="23b1d-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="23b1d-103">A classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fornece dois métodos para excluir arquivos de armazenamento isolado:</span><span class="sxs-lookup"><span data-stu-id="23b1d-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="23b1d-104">O método de instância <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> não recebe qualquer argumento e exclui o armazenamento que o chama.</span><span class="sxs-lookup"><span data-stu-id="23b1d-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="23b1d-105">Nenhuma permissão é necessária para essa operação.</span><span class="sxs-lookup"><span data-stu-id="23b1d-105">No permissions are required for this operation.</span></span> <span data-ttu-id="23b1d-106">Qualquer código que possa acessar o armazenamento pode excluir qualquer ou todos os dados dentro dele.</span><span class="sxs-lookup"><span data-stu-id="23b1d-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="23b1d-107">O método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> usa o valor de enumeração <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> e exclui todos os armazenamentos para o usuário que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="23b1d-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="23b1d-108">Esta operação exige a permissão <xref:System.Security.Permissions.IsolatedStorageFilePermission> para o valor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="23b1d-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b1d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23b1d-109">Example</span></span>  
 <span data-ttu-id="23b1d-110">O exemplo de código a seguir demonstra o uso dos métodos <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> estático e de instância .</span><span class="sxs-lookup"><span data-stu-id="23b1d-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="23b1d-111">A classe obtém dois armazenamentos; uma é isolado para o usuário e o assembly, e o outro é isolado para o usuário, domínio e assembly.</span><span class="sxs-lookup"><span data-stu-id="23b1d-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="23b1d-112">O armazenamento de usuário, domínio e assembly é excluído chamando o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> do arquivo de armazenamento isolado `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="23b1d-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="23b1d-113">Em seguida, todos os armazenamentos restantes para o usuário são excluídos chamando o método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="23b1d-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="23b1d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23b1d-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="23b1d-115">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="23b1d-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
