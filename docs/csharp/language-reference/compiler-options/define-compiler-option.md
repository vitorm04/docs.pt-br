---
title: "/define (C# Compiler Options) | Microsoft Docs"
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
  - "/define"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-define compiler option [C#]"
  - "/define compiler option [C#]"
  - "-d compiler option [C#]"
  - "define compiler option [C#]"
  - "/d compiler option [C#]"
  - "d compiler option [C#]"
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /define (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/define** define `name` como um símbolo em todos os arquivos de código\-fonte seu programa.  
  
## Sintaxe  
  
```  
/define:name[;name2]  
```  
  
## Arguments  
 `name`, `name2`  
 O nome de um ou mais símbolos que você deseja definir.  
  
## Comentários  
 A opção de **\/define** tem o mesmo efeito que usar uma política de pré\-processador de [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) exceto que a opção do compilador é aplicado a todos os arquivos no projeto.  Um símbolo permanece definido em um arquivo de origem até que uma política de [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) no arquivo de origem remover a definição.  Quando você usa a opção \/define, uma política de `#undef` em um arquivo não tem nenhum efeito em outros arquivo de código\-fonte no projeto.  
  
 Você pode usar os símbolos criados por essa opção com [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), e [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) condicional criar arquivos de origem.  
  
 **\/d** é a forma abreviada de **\/define**.  
  
 Você pode definir várias símbolos com **\/define** usando um ponto\-e\-vírgula ou uma vírgula para separar nomes de símbolo.  Por exemplo:  
  
```  
/define:DEBUG;TUESDAY  
```  
  
 O próprio compilador C\# não define nenhum símbolo ou macro que você pode usar em seu código\-fonte; todas as definições de símbolo devem ser definidas pelo usuário.  
  
> [!NOTE]
>  O C\# `#define` não permite um símbolo é dado um valor, como em linguagens como C\+\+.  Por exemplo, `#define` não pode ser usado para criar uma macro ou para definir uma constante.  Se você precisar definir uma constante, use uma variável de `enum` .  Se você quiser criar a macro de estilo criando c, considere de backup como produtos genéricas.  Desde que as macros são notòria sujeitos a erros, C\# desabilita o uso mas fornece alternativas mais seguras.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Na guia de **Compilar** , digite o símbolo que deve ser definida na caixa de **Símbolos de compilação condicional** .  Por exemplo, se você estiver usando o exemplo de código a seguir, apenas tipo `xx` na caixa de texto.  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## Exemplo  
  
```  
// preprocessor_define.cs  
// compile with: /define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)