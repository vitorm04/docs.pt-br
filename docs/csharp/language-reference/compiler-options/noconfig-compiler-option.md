---
title: "/noconfig (C# Compiler Options) | Microsoft Docs"
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
  - "/noconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/noconfig compiler option [C#]"
  - "csc.rsp"
  - "-noconfig compiler option [C#]"
  - "noconfig compiler option [C#]"
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /noconfig (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/noconfig** informa o compilador para não criar com o arquivo de csc.rsp, que está localizado no e carregados do mesmo diretório do arquivo de csc.exe.  
  
## Sintaxe  
  
```  
/noconfig  
```  
  
## Comentários  
 As referências de arquivo de csc.rsp todos os assemblies enviados com o.NET Framework.  As referências reais que o ambiente de desenvolvimento do Visual Studio .NET inclui dependem do tipo de projeto.  
  
 Você pode modificar o arquivo de csc.rsp e especificar as opções adicionais do compilador que devem ser incluídas em cada compilação da linha de comando com o csc.exe \(exceto a opção de **\/noconfig** \).  
  
 O compilador processa as opções transmitidas ao último comando de **csc** .  Em virtude disso, qualquer opção na linha de comando substituirá a configuração da mesma opção no arquivo de csc.rsp.  
  
 Se você não quiser que o compilador para navegar e para usar as configurações no csc.rsp arquivo, especifique **\/noconfig**.  
  
 Essa opção do compilador não estiver disponível no Visual Studio e não pode ser modificada programaticamente.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)