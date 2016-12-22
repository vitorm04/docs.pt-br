---
title: "/warnaserror (C# Compiler Options) | Microsoft Docs"
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
  - "/warnaserror"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/warnaserror compiler option [C#]"
  - "-warnaserror compiler option [C#]"
  - "warnaserror compiler option [C#]"
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warnaserror (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/warnaserror\+** trata todos os avisos como erros  
  
## Sintaxe  
  
```  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## Comentários  
 Todas as mensagens que normalmente são relatados como avisos são relatados como erros em vez, e o processo de compilação são paralisados \(nenhum arquivo de saída é compilada\).  
  
 Por padrão, **\/warnaserror\-** é aplicado, o que causa avisos não evitar a geração de um arquivo de saída.  **\/warnaserror**, que é igual a **\/warnaserror\+**, gerencie avisos ser tratado como erros.  
  
 Opcionalmente, se você quiser apenas alguns avisos específicos ser tratados como erros, você pode especificar uma lista separada por vírgulas de números de aviso para tratar como erros.  
  
 Use [\/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) para especificar o nível de avisos que você deseja que o compilador para exibir.  Use [\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) para desabilitar alguns avisos.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Modifique a propriedade de **Tratar Avisos como Erros** .  
  
     Para definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.  
  
## Exemplo  
 Criar `in.cs` e fazer com que o compilador não exibir nenhum aviso:  
  
```  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)