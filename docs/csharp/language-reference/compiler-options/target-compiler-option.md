---
title: "/target (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/target"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#]"
  - "/target compiler options [C#]"
  - "assemblies [C#], compiling"
  - "-target compiler options [C#]"
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção do compilador de **\/target** pode ser especificada em uma de quatro formas:  
  
 [\/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Para criar um arquivo.exe para aplicativos de [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] .  
  
 [\/target: exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md)  
 Para criar um arquivo.exe.  
  
 [\/target: biblioteca](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Para criar uma biblioteca de códigos.  
  
 [\/target: módulo](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Para criar um módulo.  
  
 [\/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Para criar um programa do windows.  
  
 [\/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Para criar um arquivo de .winmdobj intermediário.  
  
 A menos que você especifique **\/target:module**, **\/target** causa um manifesto do assembly do .NET Framework. a ser colocado em um arquivo de saída.  Para obter mais informações, consulte [Assemblies no Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md) e [Atributos comuns](../Topic/Common%20Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 O manifesto do assembly será colocado no primeiro arquivo de saída de .exe na compilação ou no primeiro DLL, se não houver nenhum arquivo de saída de .exe.  Por exemplo, na linha de comando, o manifesto será colocado em `1.exe`:  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 O compilador cria apenas um manifesto do assembly pela compilação.  Informações sobre todos os arquivos em uma compilação é colocada no manifesto do assembly.  Todos os arquivos de saída exceto aqueles criados com **\/target:module** possam conter um manifesto do assembly.  Ao gerar vários arquivos de saída na linha de comando, apenas um assembly manifesto pode ser criado e deve entrar no primeiro arquivo de saída especificado na linha de comando.  Independentemente do primeiro arquivo de saída for \(**\/target:exe**, **\/target:winexe**, **\/target:library** ou **\/target:module**\), todos os outros arquivos de saída gerados na mesma criação devem ser**\/target:module**módulos \(\).  
  
 Se você criar um assembly, você pode indicar que todo ou parte do código é compatível com CLS o atributo de <xref:System.CLSCompliantAttribute> .  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Para obter mais informações sobre como definir esta opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [\/subsystemversion \(Specify minimum subsystem version\)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)