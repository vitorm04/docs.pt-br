---
title: "/doc (C# Compiler Options) | Microsoft Docs"
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
  - "FileProperties.BuildAction"
  - "/doc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "comments, C# code"
  - "XML documentation [C#], comments in source files"
  - "doc compiler option [C#]"
  - "Visual C#, XML documentation for"
  - "-doc compiler option [C#]"
  - "/doc compiler option [C#]"
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /doc (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/doc** permite que você coloque comentários sobre a documentação do em um arquivo XML.  
  
## Sintaxe  
  
```  
/doc:file  
```  
  
## Arguments  
 `file`  
 O arquivo de saída XML para, que é populado com os comentários em arquivos de origem da compilação.  
  
## Comentários  
 Em arquivos de origem, os comentários sobre a documentação que precedem o seguinte podem ser processados e adicionado ao arquivo XML:  
  
-   Tipos definidos pelo usuário como [classe](../../../csharp/language-reference/keywords/class.md), [delegado](../../../csharp/language-reference/keywords/delegate.md), ou [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   Membros como um campo, [evento](../../../csharp/language-reference/keywords/event.md), [propriedade](../../../csharp/programming-guide/classes-and-structs/using-properties.md), ou o método  
  
 O arquivo de origem que contém o main é o primeiro saída em XML.  
  
 Para usar o arquivo .xml gerado para uso com o recurso de [O IntelliSense](/visual-studio/ide/using-intellisense) , deixe o nome do arquivo .xml ser igual ao assembly desejar oferecer suporte e certificar\-se no arquivo .xml estiver no mesmo diretório que o assembly.  Portanto, quando o assembly for referenciado no projeto do Visual Studio, o arquivo .xml for encontrado também.  [Fornecendo comentários de código](/visual-studio/ide/supplying-xml-code-comments) consulte e para obter mais informações.  
  
 A menos que você compile com [\/target: módulo](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` conterá \<o assembly\>\<\/marcas do assembly\> que especifica o nome do arquivo que contém o manifesto do assembly para o arquivo de saída de compilação.  
  
> [!NOTE]
>  A opção \/doc se aplica a todos os arquivos de entrada; ou, se definido em configurações de projeto, todos os arquivos no projeto.  Para desabilitar avisos relacionados a comentários sobre a documentação para um arquivo específico ou a seção de código, use [aviso de \#pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Consulte [Marcas recomendadas para comentários sobre a documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) para as maneiras que gerenciam a documentação de comentários em seu código.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na guia **Build**.  
  
3.  Modifique a propriedade de **Arquivo de Documentação XML** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)