---
title: "Como ler um arquivo de texto (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StreamReader.ReadToEnd"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lendo dados, arquivos de texto"
  - "lendo arquivos de texto"
  - "arquivos de texto, lendo"
  - "arquivos de texto, gravando em"
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como ler um arquivo de texto (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo lê o conteúdo de um arquivo de texto usando os métodos estáticos <xref:System.IO.File.ReadAllText%2A> e <xref:System.IO.File.ReadAllLines%2A> da classe de <xref:System.IO.File?displayProperty=fullName> .  
  
 Para um exemplo que usa <xref:System.IO.StreamReader>, consulte [Como ler um arquivo de texto uma linha de cada vez](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Os arquivos que são usados em esse exemplo são criados no tópico [Como escrever em um arquivo de texto](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## Exemplo  
 [!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## Compilando o código  
 Copie e cole o código em um aplicativo de console C\#.  
  
 Se você não estiver usando arquivos de texto de [Como escrever em um arquivo de texto](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), substitua o argumento para `ReadAllText` e a `ReadAllLines` apropriado com o caminho e o nome de arquivo no seu computador.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo não existe ou não existe no local especificado.  Verifique o caminho e a ortografia do nome de arquivo.  
  
## Segurança do .NET Framework  
 Não confie no nome de um arquivo para determinar o conteúdo do arquivo.  Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo fonte C\#.  
  
## Consulte também  
 <xref:System.IO?displayProperty=fullName>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)