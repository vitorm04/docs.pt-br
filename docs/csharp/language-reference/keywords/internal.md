---
title: "internal (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "internal_CSharpKeyword"
  - "internal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave interna [C#]"
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# internal (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave de `internal` é [modificador de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) para tipos e membros do tipo.  Tipos e membros internos são acessíveis somente dentro dos arquivos no mesmo assembly, como em este exemplo:  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 Tipos e membros que têm o modificador de acesso `protected internal` podem ser acessados do assembly atual ou dos tipos que são derivados da classe recipiente.  
  
 Para uma comparação de `internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Para obter mais informações sobre assemblies, consulte [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Um uso comum de acesso em desenvolvimento interno é baseado em componentes porque ela permite que um grupo de componentes para cooperar de uma maneira particular sem ser exposta para o resto do código do aplicativo.  Por exemplo, uma estrutura para criar interfaces de usuário gráficas pode fornecer `Control` e as classes de `Form` que cooperam usando membros com acesso interno.  Como esses membros são compilados, não são expostos a código que é a estrutura.  
  
 Sido um erro para fazer referência a um tipo ou membro com acesso interno fora do assembly no qual foi definido.  
  
## Exemplo  
 Este exemplo contém dois arquivos, `Assembly1.cs` e \_`a.cs`de `Assembly1`.  O primeiro arquivo contém uma classe base interna, `BaseClass`.  Em o segundo arquivo, uma tentativa de criar uma instância `BaseClass` irá gerar um erro.  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## Exemplo  
 Em esse exemplo, use os mesmos arquivos que você usou no exemplo 1, e altere a acessibilidade no nível de `BaseClass` a `public`.  Também alterar a acessibilidade no nível do membro `IntM` a `internal`.  Em esse caso, você pode criar uma instância da classe, mas você não pode acessar o membro interno.  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)