---
title: "Como obter repositórios para o armazenamento isolado"
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
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb0b877aa0f4cee36bd1f8c1cea624cf9368fbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="0f6ac-102">Como obter repositórios para o armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="0f6ac-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="0f6ac-103">Um armazenamento isolado expõe um sistema de arquivos virtual dentro de um compartimento de dados.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="0f6ac-104">O <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe fornece vários métodos para interagir com um armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="0f6ac-105">Para criar e recuperar os repositórios, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fornece três métodos estáticos:</span><span class="sxs-lookup"><span data-stu-id="0f6ac-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="0f6ac-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Retorna o armazenamento é isolado por usuário e assembly.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="0f6ac-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>Retorna o armazenamento é isolado por domínio e assembly.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="0f6ac-108">Ambos os métodos de recuperar um armazenamento que pertence ao código do qual eles são chamados.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="0f6ac-109">O método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> retorna um armazenamento isolado que é especificado pela passagem de uma combinação de parâmetros de escopo.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="0f6ac-110">O código a seguir retorna um repositório que é isolado por usuário, o assembly e o domínio.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="0f6ac-111">Você pode usar o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método para especificar que um armazenamento deve transitar com um perfil de usuário móvel.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="0f6ac-112">Para obter detalhes sobre como configurar isso, consulte [tipos de isolamento](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="0f6ac-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="0f6ac-113">Armazenamentos isolados obtidos em diferentes assemblies são, por padrão, os repositórios diferentes.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="0f6ac-114">Você pode acessar o armazenamento de um assembly diferente ou um domínio, passando o evidências de assembly ou domínio nos parâmetros do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="0f6ac-115">Isso exige a permissão para acessar o armazenamento isolado por identidade do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="0f6ac-116">Para obter mais informações, consulte o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> sobrecargas do método.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="0f6ac-117">O <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> métodos retornam um <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objeto.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="0f6ac-118">Para ajudá-lo a decidir qual tipo de isolamento é mais apropriado para sua situação, consulte [tipos de isolamento](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="0f6ac-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="0f6ac-119">Quando você tiver um objeto de arquivo de armazenamento isolado, você pode usar os métodos de armazenamento isolado para ler, gravar, criar e excluir arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="0f6ac-120">Não há nenhum mecanismo que evita que o código passando um <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objeto para o código que não tem acesso suficiente para obter o armazenamento em si.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="0f6ac-121">Identidades de domínio e assembly e permissões de armazenamento isolado são verificadas apenas quando uma referência a um <xref:System.IO.IsolatedStorage.IsolatedStorage> objeto é obtido, normalmente no <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="0f6ac-122">Proteger referências a <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objetos é, portanto, a responsabilidade do código que usa essas referências.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6ac-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f6ac-123">Example</span></span>  
 <span data-ttu-id="0f6ac-124">O código a seguir fornece um exemplo simples de uma classe obtendo um armazenamento que é isolado por usuário e assembly.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="0f6ac-125">O código pode ser alterado para recuperar um armazenamento que é isolado por usuário, domínio e assembly adicionando <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> aos argumentos que o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> passa de método.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="0f6ac-126">Depois de executar o código, você pode confirmar que um armazenamento foi criado digitando **StoreAdm /LIST** na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="0f6ac-127">Isso executará o [ferramenta de armazenamento isolado (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) e lista todos os armazenamentos isolados atualmente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="0f6ac-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0f6ac-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f6ac-128">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="0f6ac-129">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="0f6ac-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="0f6ac-130">Tipos de isolamento</span><span class="sxs-lookup"><span data-stu-id="0f6ac-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)  
 [<span data-ttu-id="0f6ac-131">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="0f6ac-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
