---
title: "Como obter informações sobre arquivos, pastas e unidades (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 16950f835938846804ade1a8ad23d907aa69b9c3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Como obter informações sobre arquivos, pastas e unidades (Guia de Programação em C#)
No .NET Framework, você pode acessar informações do sistema de arquivos usando as classes a seguir:  
  
-   <xref:System.IO.FileInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DriveInfo?displayProperty=fullName>  
  
-   <xref:System.IO.Directory?displayProperty=fullName>  
  
-   <xref:System.IO.File?displayProperty=fullName>  
  
 As classes <xref:System.IO.FileInfo> e <xref:System.IO.DirectoryInfo> representam um arquivo ou diretório e contêm propriedades que expõem muitos dos atributos de arquivo que têm suporte pelo sistema de arquivos NTFS. Elas também contêm métodos para abrir, fechar, mover e excluir arquivos e pastas. Você pode criar instâncias dessas classes passando uma cadeia de caracteres que representa o nome do arquivo, pasta ou unidade para o construtor:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Você também pode obter os nomes de arquivos, pastas ou unidades usando chamadas para <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=fullName>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=fullName> e <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=fullName>.  
  
 As classes <xref:System.IO.Directory?displayProperty=fullName> e <xref:System.IO.File?displayProperty=fullName> fornecem métodos estáticos para recuperar informações sobre diretórios e arquivos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra várias maneiras de acessar informações sobre arquivos e pastas.  
  
 [!code-cs[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando você processa cadeias de caracteres do caminho especificado pelo usuário, você também deve tratar exceções para as seguintes condições:  
  
-   O nome do arquivo está malformado. Por exemplo, ele contém caracteres inválidos ou somente espaço em branco.  
  
-   O nome do arquivo é nulo.  
  
-   O nome de arquivo é maior que o comprimento máximo definido pelo sistema.  
  
-   O nome de arquivo contém dois-pontos (:).  
  
 Se o aplicativo não tem permissões suficientes para ler o arquivo especificado, o método `Exists` retorna `false` independentemente de se um caminho existe, o método não gera uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO?displayProperty=fullName>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)
