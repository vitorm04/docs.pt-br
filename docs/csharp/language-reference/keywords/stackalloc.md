---
title: "stackalloc (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "stackalloc_CSharpKeyword"
  - "stackalloc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave stackalloc [C#]"
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# stackalloc (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `stackalloc` em um contexto de código não seguro, a palavra\-chave é usada para alocar um bloco de memória na pilha.  
  
```  
int* block = stackalloc int[100];  
```  
  
## Comentários  
 A palavra\-chave é válida somente no inicializadores de variáveis locais.  O código a seguir faz com que os erros do compilador.  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 Porque os tipos de ponteiro estão envolvidos, `stackalloc` requer  [não seguros](../../../csharp/language-reference/keywords/unsafe.md) contexto.  Para obter mais informações, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc`é como [\_alloca](/visual-cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.  
  
 O exemplo a seguir calcula e exibe os 20 primeiros números na seqüência de Fibonacci.  Cada número é a soma dos dois números anteriores.  No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocada na pilha, não o heap.  O endereço do bloco é armazenado no ponteiro `fib`.  Essa memória não estará sujeito à coleta de lixo e, portanto, não precisa ser fixado \(usando  [fixa](../../../csharp/language-reference/keywords/fixed-statement.md)\).  O tempo de vida do bloco de memória é limitado à vida útil do método que a define.  Você não pode liberar a memória antes do método retorna.  
  
## Exemplo  
 [!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## Segurança  
 Código não seguro é menos seguro do que as alternativas de seguras.  No entanto, o uso de `stackalloc` automaticamente habilita recursos de detecção de saturação de buffer no common language runtime \(CLR\).  Se for detectada uma saturação de buffer, o processo é encerrado assim que possível para minimizar a chance de que o código mal\-intencionado seja executado.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)