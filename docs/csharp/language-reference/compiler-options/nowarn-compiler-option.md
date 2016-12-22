---
title: "/nowarn (C# Compiler Options) | Microsoft Docs"
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
  - "/nowarn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowarn compiler option [C#]"
  - "/nowarn compiler option [C#]"
  - "-nowarn compiler option [C#]"
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /nowarn (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/nowarn** permite suprimir o compilador de exibir um ou mais avisos.  Vários números diferentes de aviso com uma vírgula.  
  
## Sintaxe  
  
```  
/nowarn:number1[,number2,...]  
```  
  
## Arguments  
 `number1`, `number2`  
 Números de aviso que você deseja que o compilador para suprimir.  
  
## Comentários  
 Você deve especificar apenas a parte numérica do identificador de aviso.  Por exemplo, se você deseja suprimir CS0028, você pode especificar `/nowarn:28`.  
  
 O compilador ignorará silenciosamente os números de aviso passados para `/nowarn` que eram válidos nas versões anteriores, mas que foram removidos do compilador.  Por exemplo, CS0679 era válido no compilador do Visual Studio .NET 2002. mas foi descartado.  
  
 Os seguintes avisos não podem ser suprimidos pela opção de `/nowarn` :  
  
-   Aviso do compilador \(nível 1\) CS2002  
  
-   Aviso do compilador \(nível 1\) CS2023  
  
-   Aviso do compilador \(nível 1\) CS2029  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** para o projeto.  Para obter detalhes, consulte [Página de Compilação, Designer de Projeto \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Modifique a propriedade de **Suprimir avisos** .  
  
 Para obter informações sobre como configurar esta opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)