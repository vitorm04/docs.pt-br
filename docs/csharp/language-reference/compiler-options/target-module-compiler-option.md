---
title: "/target:module (C# Compiler Options) | Microsoft Docs"
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
  - "/target:module"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:module"
  - "target compiler options [C#], /target:module"
  - "/target compiler options [C#], /target:module"
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:module (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Esta opção faz com que o compilador não gerencia um manifesto do assembly.  
  
## Sintaxe  
  
```  
/target:module  
```  
  
## Comentários  
 Por padrão, o arquivo de saída criado compilando com essa opção terá uma extensão de .netmodule.  
  
 Um arquivo que não tem um manifesto do assembly não pode ser carregado pelo .NET Framework Common Language Runtime.  Entretanto, esse arquivo pode ser inserido no manifesto do assembly de um assembly por meio de [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Se mais de um módulo é criado em uma única compilação, [interno](../../../csharp/language-reference/keywords/internal.md) em um módulo estará disponível para outros módulos da compilação.  Quando o código de um módulo faz referência `internal` em outro módulo, então tanto os módulos devem ser inseridos em um manifesto do assembly, por meio de **\/addmodule**.  
  
 Criar um módulo não tem suporte no ambiente de desenvolvimento do Visual Studio.  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemplo  
 Criar `in.cs`, criando `in.netmodule`:  
  
```  
csc /target:module in.cs  
```  
  
## Consulte também  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)