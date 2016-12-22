---
title: "Como: determinar se um arquivo &#233; um Assembly (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: determinar se um arquivo &#233; um Assembly (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um arquivo é um assembly somente se ele é gerenciado e contém uma entrada de assembly em seus metadados. Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto de um assembly](../Topic/Assembly%20Manifest.md).  
  
### Como determinar manualmente se um arquivo é um assembly  
  
1.  Iniciar o [Ildasm.exe \(IL Disassembler\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md).  
  
2.  Carregar o arquivo que você deseja testar.  
  
3.  Se **ILDASM** relatórios que o arquivo não é um arquivo executável portátil \(PE\), não é um assembly. Para obter mais informações, consulte o tópico [Como exibir o conteúdo de um assembly](../Topic/How%20to:%20View%20Assembly%20Contents.md).  
  
### Como determinar programaticamente se um arquivo é um assembly  
  
1.  Chamar o <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> método, passando o caminho completo e o nome do arquivo que você está testando.  
  
2.  Se um <xref:System.BadImageFormatException> exceção é lançada, o arquivo não é um assembly.  
  
## Exemplo  
 Este exemplo testa uma DLL para verificar se ele é um assembly.  
  
```  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```  
  
 O <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> método carrega o arquivo de teste e libera quando a informação é lida.  
  
## Consulte também  
 <xref:System.Reflection.AssemblyName>   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Assemblies e o Cache de Assembly Global \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)