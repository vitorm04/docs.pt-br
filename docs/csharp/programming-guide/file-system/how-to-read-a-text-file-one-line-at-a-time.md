---
title: "Como ler um arquivo de texto uma linha de cada vez (Visual C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lendo arquivos de texto, linha por linha"
  - "método ReadLine [C#]"
  - "arquivos de texto [C#]"
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como ler um arquivo de texto uma linha de cada vez (Visual C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo lê o conteúdo de um arquivo de texto, uma linha por vez, em uma seqüência de caracteres usando o `ReadLine` método da `StreamReader` classe.  Cada linha de texto é armazenada na seqüência de `line` e exibidos na tela.  
  
## Exemplo  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## Compilando o código  
 Copie o código e colá\-lo para o `Main` o método de um aplicativo de console.  
  
 Substitua `"c:\test.txt"` com o nome do arquivo real.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo pode não existir.  
  
## Segurança do .NET Framework  
 Não faça decisões sobre o conteúdo do arquivo com base no nome do arquivo.  Por exemplo, o arquivo `myFile.cs` não pode ser um arquivo de origem C\#.  
  
## Consulte também  
 <xref:System.IO?displayProperty=fullName>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)