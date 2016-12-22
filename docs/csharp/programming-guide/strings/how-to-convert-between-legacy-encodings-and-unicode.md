---
title: "Como converter entre codifica&#231;&#245;es herdadas e Unicode (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversões [C#], codificação herdada para unicode"
  - "cadeias de caracteres [C#], convertendo entre codificações"
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como converter entre codifica&#231;&#245;es herdadas e Unicode (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No C\#, todas as strings na memória são codificadas como Unicode \(UTF\-16\).  Quando você trazer dados de armazenamento em um `string` de objeto, os dados são automaticamente convertidos para UTF\-16.  Se os dados contêm apenas os valores ASCII de 0 a 127, a conversão não requer nenhum esforço extra de sua parte.  No entanto, se o texto de origem contiver valores de byte ASCII estendidos \(128 a 255\), os caracteres estendidos serão interpretados pelo padrão de acordo com a página de código atual.  Para especificar que o texto de origem deve ser interpretado de acordo com a uma página de código diferente, use o <xref:System.Text.Encoding?displayProperty=fullName> de classe como mostrado no exemplo a seguir.  
  
## Exemplo  
 O exemplo a seguir mostra como converter um arquivo de texto a ser codificado em ASCII de 8 bits, interpretar o texto de origem de acordo com 737 de página de código do Windows.  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## Consulte também  
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)