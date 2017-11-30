---
title: "Como antecipar condições de espaço insuficiente com o armazenamento isolado"
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
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
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
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d813522d0aeb9bf37582c167760d44268df27039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Como antecipar condições de espaço insuficiente com o armazenamento isolado
O código que usa armazenamento isolado é restrito por um [cota](../../../docs/standard/io/isolated-storage.md#quotas) que especifica o tamanho máximo para o compartimento de dados no qual isolar arquivos de armazenamento e diretórios existem. A cota é definida pela política de segurança e é configurável por administradores. Se o máximo permitido de tamanho foi excedido ao tentar gravar dados, um <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção será lançada e a operação falhará. Isso ajuda a evitar ataques de negação de serviço que podem fazer com que o aplicativo recuse solicitações porque o armazenamento de dados é preenchido.  
  
 Para ajudá-lo a determinar se uma determinada tentativa de gravação provavelmente falhará por esse motivo, o <xref:System.IO.IsolatedStorage.IsolatedStorage> classe fornece três propriedades somente leitura: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, e <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Você pode usar essas propriedades para determinar se a gravação no armazenamento fará com que o tamanho máximo permitido de armazenamento seja excedido. Tenha em mente que o armazenamento isolado pode ser acessada simultaneamente; Portanto, quando você calcular a quantidade de armazenamento restante, o espaço de armazenamento foi consumido quando que você tenta gravar no repositório. No entanto, você pode usar o tamanho máximo do repositório para ajudar a determinar se o limite superior no armazenamento disponível está prestes a ser atingido.  
  
 O <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> propriedade depende da evidência do assembly funcione corretamente. Por esse motivo, você deve recuperar esta propriedade somente em <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objetos que foram criados usando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>objetos que foram criados de qualquer outra forma (por exemplo, os objetos que foram retornados do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> método) não retornará um tamanho máximo preciso.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir obtém um armazenamento isolado, cria alguns arquivos e recupera o <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> propriedade. O espaço restante é reportado em bytes.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)  
 [Como obter repositórios para o armazenamento isolado](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
