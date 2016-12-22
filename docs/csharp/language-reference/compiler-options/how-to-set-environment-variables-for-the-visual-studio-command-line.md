---
title: "How to: Set Environment Variables for the Visual Studio Command Line | Microsoft Docs"
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
  - "cs.build.commandline"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "csc.exe, command-line builds"
  - "Visual C#, command-line builds"
  - "command-line compilers, Visual C#"
  - "Vsvars32.bat"
  - "builds [C#], command-line"
  - "compilers, invoking from command line"
  - "Vcvars32.bat file"
  - "command line [C#], building from"
  - "Visual C# compiler, enabling"
  - "compiling source code, from command line"
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Set Environment Variables for the Visual Studio Command Line
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O arquivo vsvars32. bat define as variáveis de ambiente adequadas para permitir compilações de linha de comando.  Para obter mais informações sobre vsvars32. bat, consulte [artigo da Base de dados de Conhecimento Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).  
  
 Se a versão atual do Visual Studio estiver instalada em um computador que também tem uma versão anterior do Visual Studio, você não deve executar vsvars32. bat ou vcvars32 de versões diferentes na mesma janela do Prompt de comando.  
  
### Para executar VSVARS32.BAT  
  
1.  Do **Iniciar** menu, abrir o **Prompt de comando do desenvolvedor para VS2012**.  
  
2.  Alterar para os arquivos de Programas\\Microsoft Visual Studio *versão*\\Common7\\Tools ou arquivos de programas \(x86\) \\Microsoft Visual Studio *versão*\\Common7\\Tools subdiretório da sua instalação.  
  
3.  Execute vsvars32. bat digitando VSVARS32.  
  
    > [!CAUTION]
    >  Vsvars32. bat pode variar de um computador para outro.  Não substitua um arquivo vsvars32. bat danificado ou com um vsvars32. bat em outro computador.  Em vez disso, execute a instalação novamente para substituir o arquivo ausente.  
  
## Consulte também  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)