---
title: "/codepage (C# Compiler Options) | Microsoft Docs"
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
  - "/codepage"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/codepage compiler option [C#]"
  - "codepage compiler option [C#]"
  - "-codepage compiler option [C#]"
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /codepage (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Esta opção especifica que página de código a ser usada durante a compilação se a página não é necessária a página de código padrão atual do sistema.  
  
## Sintaxe  
  
```  
/codepage:id  
```  
  
## Arguments  
 `id`  
 A ID da página de código a ser usada para todos os arquivos de código\-fonte na compilação.  
  
## Comentários  
 Se você criar um ou mais arquivos de origem que não foram criados para usar a página de código padrão no computador, você poderá usar a opção de especificar que **\/codepage** página de código deve ser usada.  **\/codepage** se aplica a todos os arquivos de código\-fonte em sua compilação.  
  
 Se o arquivo de origem foi criado com a mesma página de código que está em vigor em seu computador ou se os arquivos de código\-fonte foram criados com UNICODE ou UTF\-8, você não precisa usar **\/codepage**.  
  
 Consulte [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) para obter informações sobre como encontrar quais páginas de código têm suporte no sistema.  
  
 Essa opção do compilador não estiver disponível no Visual Studio e não pode ser modificada programaticamente.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)