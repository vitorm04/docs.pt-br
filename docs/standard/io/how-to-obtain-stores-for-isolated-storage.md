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
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Como obter repositórios para o armazenamento isolado
Um armazenamento isolado expõe um sistema de arquivos virtual dentro de um compartimento de dados. O <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe fornece vários métodos para interagir com um armazenamento isolado. Para criar e recuperar os repositórios, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fornece três métodos estáticos:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Retorna o armazenamento é isolado por usuário e assembly.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>Retorna o armazenamento é isolado por domínio e assembly.  
  
     Ambos os métodos de recuperar um armazenamento que pertence ao código do qual eles são chamados.  
  
-   O método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> retorna um armazenamento isolado que é especificado pela passagem de uma combinação de parâmetros de escopo.  
  
 O código a seguir retorna um repositório que é isolado por usuário, o assembly e o domínio.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Você pode usar o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método para especificar que um armazenamento deve transitar com um perfil de usuário móvel. Para obter detalhes sobre como configurar isso, consulte [tipos de isolamento](../../../docs/standard/io/types-of-isolation.md).  
  
 Armazenamentos isolados obtidos em diferentes assemblies são, por padrão, os repositórios diferentes. Você pode acessar o armazenamento de um assembly diferente ou um domínio, passando o evidências de assembly ou domínio nos parâmetros do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método. Isso exige a permissão para acessar o armazenamento isolado por identidade do domínio de aplicativo. Para obter mais informações, consulte o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> sobrecargas do método.  
  
 O <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> métodos retornam um <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objeto. Para ajudá-lo a decidir qual tipo de isolamento é mais apropriado para sua situação, consulte [tipos de isolamento](../../../docs/standard/io/types-of-isolation.md). Quando você tiver um objeto de arquivo de armazenamento isolado, você pode usar os métodos de armazenamento isolado para ler, gravar, criar e excluir arquivos e diretórios.  
  
 Não há nenhum mecanismo que evita que o código passando um <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objeto para o código que não tem acesso suficiente para obter o armazenamento em si. Identidades de domínio e assembly e permissões de armazenamento isolado são verificadas apenas quando uma referência a um <xref:System.IO.IsolatedStorage.IsolatedStorage> objeto é obtido, normalmente no <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método. Proteger referências a <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objetos é, portanto, a responsabilidade do código que usa essas referências.  
  
## <a name="example"></a>Exemplo  
 O código a seguir fornece um exemplo simples de uma classe obtendo um armazenamento que é isolado por usuário e assembly. O código pode ser alterado para recuperar um armazenamento que é isolado por usuário, domínio e assembly adicionando <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> aos argumentos que o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> passa de método.  
  
 Depois de executar o código, você pode confirmar que um armazenamento foi criado digitando **StoreAdm /LIST** na linha de comando. Isso executará o [ferramenta de armazenamento isolado (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) e lista todos os armazenamentos isolados atualmente para o usuário.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)  
 [Tipos de isolamento](../../../docs/standard/io/types-of-isolation.md)  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
