---
title: "Como capturar uma exce&#231;&#227;o n&#227;o compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "exceções [C#], não CLS"
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como capturar uma exce&#231;&#227;o n&#227;o compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Alguns.NET, inclusive o C \+ \+ \/ CLI, permite que os objetos lançar exceções que não derivam de <xref:System.Exception>.  Essas exceções são chamadas de  *não\-CLS exceções* ou  *Não\-exceções*.  Na [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] você não pode lançar exceções não\-CLS, mas você pode capturá\-las de duas maneiras:  
  
-   Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Por padrão, um [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] assembly captura exceções de não\-CLS como exceções dispostas.  Use este método se você precisa de acesso para a exceção original, que pode ser acessada por meio do <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> propriedade.  O procedimento neste tópico explica como capturar exceções dessa maneira.  
  
-   Dentro de um bloco catch geral \(um bloco catch sem um tipo de exceção especificado\), que é colocada após uma `catch (Exception)` ou `catch (Exception e)` bloco.  
  
     Use esse método quando você deseja realizar alguma ação \(como gravar em um arquivo de log\) em resposta a exceções não\-CLS e não é necessário o acesso às informações de exceção.  Por padrão, o common language runtime quebra todas as exceções.  Para desabilitar esse comportamento, adicione este atributo no nível do assembly em seu código, geralmente no arquivo AssemblyInfo. CS: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### Para capturar uma exceção não\-CLS  
  
1.  Dentro de um `catch(Exception e) block`, use o `as` palavra\-chave para testar se `e` pode ser convertido para um <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  A exceção original por meio de acesso a <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> propriedade.  
  
## Exemplo  
 O exemplo a seguir mostra como capturar uma exceção não\-CLS foi acionada a partir de uma biblioteca de classes escrita em C \+ \+ \/ CLR.  Observe que, neste exemplo, o [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] código de cliente sabe de antemão que o tipo de exceção sendo lançado é um <xref:System.String?displayProperty=fullName>.  Você pode converter o <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> propriedade seu tipo original de volta, desde que esse tipo é acessível a partir de seu código.  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)