---
title: "/addmodule (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/addmodule"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/addmodule compiler option [C#]"
  - "-addmodule compiler option [C#]"
  - "addmodule compiler option [C#]"
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /addmodule (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Esta opção adiciona um módulo que foi criado com o destino: opção de módulo a compilação atual.  
  
## Sintaxe  
  
```  
/addmodule:file[;file2]  
```  
  
## Arguments  
 `file`, `file2`  
 Um arquivo de saída que contém metadados.  O arquivo não pode conter um manifesto do assembly.  Para importar mais de um arquivo, nomes de arquivos separados por uma vírgula ou um ponto\-e\-vírgula.  
  
## Comentários  
 Todos os módulos adicionados com **\/addmodule** devem estar no mesmo diretório do arquivo de saída em tempo de execução.  Ou seja, você pode especificar um módulo em qualquer diretório em tempo de compilação mas o módulo deve estar no diretório de aplicativo em tempo de execução.  Se o módulo não está no diretório do aplicativo em tempo de execução, você obterá <xref:System.TypeLoadException>.  
  
 `file` não pode conter um assembly.  Por exemplo, se o arquivo de saída foi criado com [\/target: módulo](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), seus metadados podem ser importados com **\/addmodule**.  
  
 Se o arquivo de saída foi criado com um padrão de **\/target** a não ser **\/target:module**, seus metadados não podem ser importados com **\/addmodule** mas podem ser importados com [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Essa opção do compilador não estiver disponível no Visual Studio; um projeto não pode fazer referência a um módulo.  Além disso, essa opção do compilador não pode ser modificada programaticamente.  
  
## Exemplo  
 Criar o arquivo de origem `input.cs` e adicionar metadados de `metad1.netmodule` e de `metad2.netmodule` para gerar `out.exe`:  
  
```  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Assemblies de vários arquivos](../Topic/Multifile%20Assemblies.md)   
 [Como compilar um assembly de vários arquivos](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)