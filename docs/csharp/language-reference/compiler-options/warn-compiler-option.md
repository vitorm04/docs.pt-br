---
title: "/warn (C# Compiler Options) | Microsoft Docs"
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
  - "/warn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "warning level [C#]"
  - "/w compiler option [C#]"
  - "-w compiler option [C#]"
  - "-warn compiler option [C#]"
  - "/warn compiler option [C#]"
  - "w compiler option [C#]"
  - "warn compiler option [C#]"
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warn (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/warn** especifica o nível de aviso para que o compilador exibe.  
  
## Sintaxe  
  
```  
/warn:option  
```  
  
## Arguments  
 `option`  
 O nível de aviso que você deseja exibido para a compilação: Números inferiores mostram apenas avisos altos de severidade; um número mais alto que mostram mais avisos.  Os valores válidos são 0\-4:  
  
|Nível de aviso|Significado|  
|--------------------|-----------------|  
|0|Desativa a emissão de todas as mensagens de aviso.|  
|1|Exibe mensagens de aviso severas.|  
|2|Exibe avisos de nível 1 mais determinados, avisos menos severos, como avisos sobre ocultar membros da classe.|  
|3|Exibe avisos de nível 2 mais determinados, avisos menos severos, como avisos sobre as expressões que sempre são avaliadas como `true` ou a `false`.|  
|4 \(o padrão\)|Exibe todos os avisos de nível 3 mais avisos informativos.|  
  
## Comentários  
 Para obter informações sobre um erro ou um aviso, você pode pesquisar o código de erro no índice da ajuda.  Para outras formas obtenham informações sobre um erro ou um aviso, consulte [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Use [\/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) para tratar todos os avisos como erros.  Use [\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) para desabilitar alguns avisos.  
  
 **\/w** é a forma abreviada de **\/warn**.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Modifique a propriedade de **Nível de aviso** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## Exemplo  
 Criar `in.cs` e tem os avisos de nível 1 de exibição do compilador apenas:  
  
```  
csc /warn:1 in.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)