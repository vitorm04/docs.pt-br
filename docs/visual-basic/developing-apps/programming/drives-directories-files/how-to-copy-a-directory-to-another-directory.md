---
title: "Como copiar um diret&#243;rio para outro diret&#243;rio no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "diretórios [Visual Basic], copiando"
  - "pastas [Visual Basic], copiando"
  - "E/S [Visual Basic], copiando diretórios"
  - "E/S [Visual Basic], copiando pastas"
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como copiar um diret&#243;rio para outro diret&#243;rio no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Use o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> para copiar um diretório para outro diretório.  Este método copia o conteúdo do diretório, bem como o próprio diretório.  Se a estrutura de destino não existir, ela será criada.  Se um diretório com o mesmo nome existe no local de destino e `overwrite` é definida como `False`,o conteúdo dos dois diretórios será mesclado.  Você pode especificar um novo nome para o diretório durante a operação.  
  
 Ao copiar arquivos em um diretório, exceções podem ser geradas que são causadas pelo arquivo específico, como um arquivo existente durante uma mesclagem enquanto `overwrite` estiver definida como `False`.  Quando essas exceções são geradas, elas são consolidadas em uma única exceção, cuja propriedade `Data` contém entradas em que o caminho do arquivo ou pasta é a chave e a mensagem de exceção específica está contida no valor correspondente.  
  
### Para copiar um diretório para um diretório diferente  
  
-   Use o método `CopyDirectory`, especificando nomes de diretório de origem e destino.  O exemplo a seguir copia o diretório denominado `TestDirectory1` para dentro de `TestDirectory2`, sobrescrevendo arquivos existentes.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador do trecho de código, ele está localizado no **File system \- Processing Drives, Folders, and Files**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O novo nome especificado para o diretório contém dois\-pontos \(:\) ou de barra \(\\ ou \/\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido para uma das seguintes razões: ele é uma seqüência de comprimento zero, ele contém somente espaços em branco, ele contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `destinationDirectoryName` é `Nothing` ou uma cadeia de caracteres vazia \(<xref:System.ArgumentNullException>\).  
  
-   O diretório de origem não existe \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   A diretório de origem é um diretório raiz \(<xref:System.IO.IOException>\).  
  
-   O caminho combinado aponta para uma arquivo existente \(<xref:System.IO.IOException>\).  
  
-   O caminho de origem e o caminho de destino são o mesmo \(<xref:System.IO.IOException>\).  
  
-   `ShowUI` é definida como `UIOption.AllDialogs` e o usuário cancela a operação, ou um ou mais arquivos no diretório não podem ser copiados \(<xref:System.OperationCanceledException>\).  
  
-   A operação é cíclica \(<xref:System.InvalidOperationException>\).  
  
-   O caminho contém dois\-pontos \(:\) \(<xref:System.NotSupportedException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um arquivo ou nome da pasta no caminho contém dois\-pontos \(:\) ou está em formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
-   Um arquivo de destino existe mas não pode ser acessado \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>   
 [Como localizar subdiretórios com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Como obter a coleção de arquivos em um diretório](../Topic/How%20to:%20Get%20the%20Collection%20of%20Files%20in%20a%20Directory%20in%20Visual%20Basic.md)