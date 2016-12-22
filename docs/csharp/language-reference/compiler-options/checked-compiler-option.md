---
title: "/checked (C# Compiler Options) | Microsoft Docs"
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
  - "/checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "checked compiler option [C#]"
  - "-checked compiler option [C#]"
  - "/checked compiler option [C#]"
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /checked (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/checked** especifica se uma instrução aritmética de inteiro que os resultados em um valor que estão fora do intervalo do tipo de dados, e que não está no escopo de uma palavra\-chave de [verificado](../../../csharp/language-reference/keywords/checked.md) ou de [desmarcar](../../../csharp/language-reference/keywords/unchecked.md) , provocarão uma exceção em tempo de execução.  
  
## Sintaxe  
  
```  
/checked[+ | -]  
```  
  
## Comentários  
 Uma instrução aritmética de inteiro que está no escopo de uma palavra\-chave de `checked` ou de `unchecked` não está sujeita ao efeito da opção de **\/checked** .  
  
 Se uma instrução aritmética de inteiro que não está no escopo de `checked` ou aos resultados da palavra\-chave de `unchecked` em um valor fora do intervalo do tipo de dados, e **\/checked\+** \(**\/checked**\) é usado na compilação, se a instrução gerencie uma exceção em tempo de execução.  Se **\/checked\-** é usado na compilação, a instrução não faz com que uma exceção em tempo de execução.  
  
 O valor padrão desta opção é **\/checked\-**.  Um cenário para usar **\/checked\-** consiste na criação de grandes aplicativos.  As ferramentas automatizadas às vezes são usadas para compilar esses aplicativos, e essa ferramenta pode definir automaticamente **\/checked** \+.  Você pode substituir o padrão global da ferramenta especificando **\/checked\-**.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  Para obter mais informações, consulte [Página de Compilação, Designer de Projeto \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Clique no botão de **Avançado** .  
  
4.  Modifique a propriedade de **Verificação para o estouro aritmético\/estouro negativo** .  
  
 Para acessar o programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## Exemplo  
 O comando a seguir cria `t2.cs`.  O uso de `/checked` no comando especifica que qualquer instrução aritmética de inteiro no arquivo que não estão no escopo de uma palavra\-chave de `checked` ou de `unchecked` , e que resulte em um valor que esteja fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.  
  
```  
csc t2.cs /checked  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7)