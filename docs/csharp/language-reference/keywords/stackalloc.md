---
title: "stackalloc (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b9c5328bfa1b0fc9a7751763c7d728096886905
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referência de C#)
A palavra-chave `stackalloc` é usada em um contexto de código não seguro para alocar um bloco de memória na pilha.  
  
```csharp  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>Comentários  
 A palavra-chave é válida somente em inicializadores de variável locais. O código a seguir gera erros de compilador.  
  
```csharp  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 Como os tipos de ponteiro estão envolvidos, `stackalloc` requer o contexto [unsafe](../../../csharp/language-reference/keywords/unsafe.md). Para obter mais informações, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.  
  
 O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci. Cada número é a soma dos dois números anteriores. No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap. O endereço do bloco é armazenado no ponteiro `fib`. Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)). O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define. Você não pode liberar a memória antes de o método retornar.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>Segurança  
 O código não seguro é menos seguro do que as alternativas seguras. No entanto, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime). Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
