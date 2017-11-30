---
title: "Como excluir arquivos e diretórios no armazenamento isolado"
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
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Como excluir arquivos e diretórios no armazenamento isolado
Você pode excluir pastas e arquivos em um arquivo de armazenamento isolado. Em um armazenamento, nomes de arquivo e diretório são dependentes do sistema operacional e são especificados como relacionado à raiz do sistema de arquivos virtual. Eles não diferenciam maiusculas de minúsculas em sistemas operacionais Windows.  
  
 O <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> classe fornece dois métodos para excluir arquivos e diretórios: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. Um <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção é gerada se você tentar excluir um arquivo ou diretório não existe. Se você incluir um caractere curinga no nome do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> lança um <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção, e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> lança um <xref:System.ArgumentException> exceção.  
  
 O <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> método falhará se o diretório contém quaisquer arquivos ou subpastas. Você pode usar o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> métodos para recuperar os arquivos e diretórios existentes. Para obter mais informações sobre o sistema de arquivos virtual de um repositório de pesquisa, consulte [como: localizar arquivos e diretórios existentes no armazenamento isolado](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria e, em seguida, exclui vários diretórios e arquivos.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
