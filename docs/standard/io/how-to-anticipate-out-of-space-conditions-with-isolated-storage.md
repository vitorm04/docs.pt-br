---
title: 'Como: Prever condições de espaço insuficiente com o armazenamento isolado'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf5144cb1abd3a916d2b5afc361c8c96a221d47e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372289"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="ae1a8-102">Como: Prever condições de espaço insuficiente com o armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="ae1a8-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="ae1a8-103">O código que usa armazenamento isolado é restrito por uma [cota](../../../docs/standard/io/isolated-storage.md#quotas) que especifica o tamanho máximo do compartimento de dados no qual arquivos de armazenamento e diretórios isolados existem.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="ae1a8-104">A cota é definida pela política de segurança e é configurável por administradores.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="ae1a8-105">Se o tamanho máximo permitido for ultrapassado ao tentar gravar dados, uma exceção <xref:System.IO.IsolatedStorage.IsolatedStorageException> será lançada e a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="ae1a8-106">Isso ajuda a evitar ataques de negação de serviço que podem fazer com que o aplicativo recuse solicitações porque o armazenamento de dados está cheio.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="ae1a8-107">Para ajudar você a determinar se uma determinada tentativa de gravação provavelmente falhará por esse motivo, a classe <xref:System.IO.IsolatedStorage.IsolatedStorage> fornece três propriedades somente leitura: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> e <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="ae1a8-108">Você pode usar essas propriedades para determinar se a gravação no armazenamento fará com que o tamanho máximo permitido de armazenamento seja ultrapassado.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="ae1a8-109">Lembre-se de que o armazenamento isolado pode ser acessado simultaneamente; portanto, ao calcular a quantidade de armazenamento restante, o espaço de armazenamento poderá ser consumido até você tentar gravar no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="ae1a8-110">No entanto, você pode usar o tamanho máximo do armazenamento para ajudar a determinar se o limite superior no armazenamento disponível está prestes a ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="ae1a8-111">A propriedade <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> depende da evidência do funcionamento correto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="ae1a8-112">Por esse motivo, você deve recuperar essa propriedade somente em objetos <xref:System.IO.IsolatedStorage.IsolatedStorageFile> que foram criados usando o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="ae1a8-113">Os objetos <xref:System.IO.IsolatedStorage.IsolatedStorageFile> que foram criados de qualquer outra forma (por exemplo, objetos retornados do método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>) não retornarão um tamanho máximo preciso.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="ae1a8-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae1a8-114">Example</span></span>

<span data-ttu-id="ae1a8-115">O exemplo de código a seguir obtém um armazenamento isolado, cria alguns arquivos e recupera a propriedade <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="ae1a8-116">O espaço restante é relatado em bytes.</span><span class="sxs-lookup"><span data-stu-id="ae1a8-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="ae1a8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae1a8-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="ae1a8-118">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="ae1a8-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="ae1a8-119">Como: Obter repositórios para o armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="ae1a8-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
