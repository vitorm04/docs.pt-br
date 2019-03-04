---
title: 'Como: obter informações sobre arquivos, pastas e unidades – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: e2315f5bfdca05da79e5ee4d897cd06dba6f1ed1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966158"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Como: obter informações sobre arquivos, pastas e unidades (Guia de Programação em C#)
No .NET Framework, você pode acessar informações do sistema de arquivos usando as classes a seguir:  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 As classes <xref:System.IO.FileInfo> e <xref:System.IO.DirectoryInfo> representam um arquivo ou diretório e contêm propriedades que expõem muitos dos atributos de arquivo que têm suporte pelo sistema de arquivos NTFS. Elas também contêm métodos para abrir, fechar, mover e excluir arquivos e pastas. Você pode criar instâncias dessas classes passando uma cadeia de caracteres que representa o nome do arquivo, pasta ou unidade para o construtor:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Você também pode obter os nomes das unidades, pastas ou arquivos por meio de chamadas para <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> e <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 As classes <xref:System.IO.Directory?displayProperty=nameWithType> e <xref:System.IO.File?displayProperty=nameWithType> fornecem métodos estáticos para recuperar informações sobre arquivos e diretórios.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra várias maneiras de acessar informações sobre arquivos e pastas.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando você processa cadeias de caracteres do caminho especificado pelo usuário, você também deve tratar exceções para as seguintes condições:  
  
-   O nome do arquivo está malformado. Por exemplo, ele contém caracteres inválidos ou somente espaço em branco.  
  
-   O nome do arquivo é nulo.  
  
-   O nome de arquivo é maior que o comprimento máximo definido pelo sistema.  
  
-   O nome de arquivo contém dois-pontos (:).  
  
 Se o aplicativo não tem permissões suficientes para ler o arquivo especificado, o método `Exists` retorna `false` independentemente de se um caminho existe, o método não gera uma exceção.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO?displayProperty=nameWithType>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)
