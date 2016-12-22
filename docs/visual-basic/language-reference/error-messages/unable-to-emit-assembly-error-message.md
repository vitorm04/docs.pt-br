---
title: "N&#227;o foi poss&#237;vel emitir o assembly: &lt;error message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30145"
  - "bc30145"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30145"
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o foi poss&#237;vel emitir o assembly: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o Assembly Linker \(Al.exe, também conhecido como Alink\) para gerar um assembly com um manifesto, com o vinculador relatando um erro no estágio de emissão da criação do assembly.  
  
 **ID do erro:** BC30145  
  
### Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/pt-br/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para obter mais explicações e aconselhamentos.  
  
2.  Tente assinar o assembly manualmente, usando o [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) ou o [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
3.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
### Para assinar o assembly manualmente  
  
1.  Use o [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) para criar um arquivo de par de chaves pública\/privada.  
  
     Esse arquivo tem a extensão .snk.  
  
2.  Exclua a referência COM que está gerando o erro no projeto.  
  
3.  No menu **Iniciar** do Windows, aponte para **Todos os Programas**, aponte para **Microsoft Visual Studio 2008**, **Visual Studio Tools** e clique em **Visual Studio 2008 Command Prompt**.  
  
4.  Acesse o diretório onde deseja colocar o wrapper do assembly.  
  
5.  Digite o código a seguir.  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     Um exemplo do código que pode ser inserido seria o seguinte.  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     Use aspas duplas \("\) se um caminho ou arquivo contiver espaços.  
  
6.  Em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], inclua uma referência .NET Assembly para o arquivo que acabou de ser criado.  
  
## Consulte também  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/pt-br/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)   
 [Como criar um par de chaves pública\/privada](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md)   
 [Fale conosco](/visual-studio/ide/talk-to-us)