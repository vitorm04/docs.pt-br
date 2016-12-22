---
title: "/bugreport (C# Compiler Options) | Microsoft Docs"
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
  - "/bugreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/bugreport compiler option [C#]"
  - "-bugreport compiler option [C#]"
  - "bugreport compiler option [C#]"
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /bugreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que as informações de depuração deve ser colocada em um arquivo para análise posterior.  
  
## Sintaxe  
  
```  
/bugreport:file  
```  
  
## Arguments  
 `file`  
 O nome do arquivo que você deseja conter seu relatório de erros.  
  
## Comentários  
 A opção de **\/bugreport** especifica que as informações a seguir deve ser colocada em `file`:  
  
-   Uma cópia de todos os arquivos de código\-fonte na compilação.  
  
-   Uma listagem das opções do compilador usadas na compilação.  
  
-   Informações de versão sobre seu compilador, o tempo de execução, e o sistema operacional.  
  
-   Assemblies referenciados e módulos, salvos como dígitos hexadecimais, exceto os assemblies que enviam e com o.NET Framework SDK.  
  
-   Saída do compilador, se houver.  
  
-   Uma descrição do problema, que você será solicitado a.  
  
-   Uma descrição de como você considerar o problema deve ser corrigida, que você seja solicitado para.  
  
 Se essa opção for usada com **\/errorreport:prompt** ou **\/errorreport:send**, a informações no arquivo será enviada à Microsoft Corporation.  
  
 Como uma cópia de todos os arquivos de código\-fonte será colocado em `file`, talvez você queira reproduzir o suspeito de estar defeito de código no programa possível o mais curto.  
  
 Essa opção do compilador não estiver disponível no Visual Studio e não pode ser modificada programaticamente.  
  
 Observe que o conteúdo do arquivo gerado expõe o código\-fonte que pode levar a divulgação de informações inadvertida.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/errorreport \(Set Error Reporting Behavior\)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)