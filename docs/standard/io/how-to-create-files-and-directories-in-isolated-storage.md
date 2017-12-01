---
title: "Como criar arquivos e diretórios no armazenamento isolado"
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
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Como criar arquivos e diretórios no armazenamento isolado
Depois de obter um armazenamento isolado, você pode criar pastas e arquivos para armazenar dados. Em um repositório, nomes de arquivo e diretório são especificados em relação à raiz do sistema de arquivos virtual.  
  
 Para criar um diretório, use o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> método de instância. Se você especificar um subdiretório de um diretório que não existe, ambos os diretórios serão criados. Se você especificar um diretório que já existe, o método retorna sem criar um diretório, e nenhuma exceção é lançada. No entanto, se você especificar um nome de diretório que contém caracteres inválidos, uma <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção será lançada.  
  
 Para criar um arquivo, use o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> método.  
  
 No sistema operacional Windows, arquivo de armazenamento isolado e diretório nomes diferenciam maiusculas de minúsculas. Ou seja, se você criar um arquivo chamado `ThisFile.txt`e, em seguida, criar outro arquivo chamado `THISFILE.TXT`, somente um arquivo é criado. O nome do arquivo mantém seu capitalização original para fins de exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra como criar arquivos e diretórios em um armazenamento isolado.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
