---
title: "Operadores condicionais nulos (C# e Visual Basic) | Microsoft Docs"
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
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operadores condicionais nulos (C# e Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usada para testar null antes de executar um acesso de membro \(`?.`\) ou índice \(`?[`\) operação.  Esses operadores ajudarão\-lo a escrever menos código para lidar com null verifica, especialmente em ordem decrescente em estruturas de dados.  
  
```c#  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
```vb  
Dim length = customers?.Length  ‘’ null if customers is null  
Dim first as Customer = customers?(0);  ‘’ null if customers is null  
Dim count as Integer? = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
 O último exemplo demonstra que os operadores de condição null são curto\-circuito.  Se uma operação em uma cadeia de operação de índice e de acesso de membro condicional retorna null, o restante da execução da cadeia será interrompida.  Outras operações com menor precedência na expressão de continuam.  Por exemplo, `E` a seguir sempre é executado e o `??` e `==` operações são executadas.  
  
```vb-c#  
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
  
```  
  
 Outro uso para o acesso do membro de condição nulo é chamando delegados de forma segura para thread com muito menos código.  O método antigo requer código semelhante ao seguinte:  
  
```c#  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…)  
  
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
  
```  
  
 A nova forma é muito mais simples:  
  
```vb-c#  
PropertyChanged?.Invoke(e)  
  
```  
  
 A nova forma é thread\-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado na variável temporária.  
  
 Você precisa chamar explicitamente o `Invoke` método porque não há nenhuma sintaxe de invocação de delegado nulo condicional `PropertyChanged?(e)`.  Havia muitas situações de análise ambíguas para permitir que ele.  
  
## Especificações da linguagem  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 Para obter mais informações, consulte o [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)   
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)