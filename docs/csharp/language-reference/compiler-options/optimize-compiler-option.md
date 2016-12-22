---
title: "/optimize (C# Compiler Options) | Microsoft Docs"
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
  - "/optimize"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/optimize compiler option [C#]"
  - "-o compiler option [C#]"
  - "optimize compiler option [C#]"
  - "/o compiler option [C#]"
  - "-optimize compiler option [C#]"
  - "compiler optimization [C#]"
  - "o compiler option [C#]"
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /optimize (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/optimize** habilita ou desabilita as otimizações executadas pelo compilador para fazer seu arquivo de saída menor, mais rapidamente, e mais eficiente.  
  
## Sintaxe  
  
```  
/optimize[+ | -]  
```  
  
## Comentários  
 **\/optimize** também informa Common Language Runtime para otimizar o código em tempo de execução.  
  
 Por padrão, as otimizações são desabilitadas.  Especifique **\/optimize\+** para habilitar otimizações.  
  
 Ao criar um módulo a ser usado por um assembly, use as mesmas configurações de **\/optimize** a aquelas de assembly.  
  
 **\/o** é a forma abreviada de **\/optimize**.  
  
 É possível combinar as opções de **\/optimize** e de [\/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) .  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Modifique a propriedade de **Otimizar código** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## Exemplo  
 Criar `t2.cs` e habilitar otimizações de compilador:  
  
```  
csc t2.cs /optimize  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)