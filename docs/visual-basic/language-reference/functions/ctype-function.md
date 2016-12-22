---
title: "Fun&#231;&#227;o CType (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.CType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "resultados de conversão de expressão"
  - "conversões de tipo de dados explícitos"
  - "Função CType"
  - "conversões de expressão"
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fun&#231;&#227;o CType (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Retorna o resultado da conversão explícita de uma expressão em um tipo de dados, objeto, classe ou interface especificada.  
  
## Sintaxe  
  
```  
CType(expression, typename)  
```  
  
## Partes  
 `expression`  
 Qualquer expressão válida.  Se o valor `expression` está fora do intervalo permitido por `typename`, o Visual Basic gera uma exceção.  
  
 `typename`  
 Qualquer expressão que é legal dentro de uma cláusula `As` em uma instrução `Dim`, isto é, o nome de qualquer tipo de dados, objeto, estrutura, classe ou interface.  
  
## Comentários  
  
> [!TIP]
>  Você também pode usar as seguintes funções para executar uma conversão de tipos:  
>   
>  -   A conversão de tipos funciona como `CByte`, `CDbl`, e `CInt` que executa uma conversão para um tipo de dados específico.  Para obter mais informações, consulte [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).  Esses operadores exigem que um tipo herde de outro tipo ou implemente outro tipo.  Podem fornecer um desempenho de alguma forma melhor do que `CType` ao converterem de e para o tipo de dados `Object`.  
  
 `CType` é compilado embutido, o que significa que o código de conversão é parte do código que avalia a expressão.  Em alguns casos, o código é executado mais rápido porque nenhum procedimento é chamado para realizar a conversão.  
  
 Se nenhuma conversão é definida de `expression` para `typename` \(por exemplo, `Integer` para `Date`\), o Visual Basic exibe uma mensagem de erro em tempo de compilação.  
  
 Se uma conversão falhar em tempo de execução, a exceção apropriada é lançada.  Se uma conversão de redução falhar, <xref:System.OverflowException> é o resultado mais comum.  Se a conversão é indefinida, um <xref:System.InvalidCastException> em lançada.  Por exemplo, isso pode acontecer se `expression` for do tipo `Object` e seu tipo de tempo de execução não tiver nenhuma conversão para o `typename`.  
  
 Se o tipo de dado de `expression` ou de `typename` for uma classe ou uma estrutura que você definiu, você poderá definir `CType` na classe ou na estrutura como um operador de conversão.  Isso faz com que o `CType` atue como um *operador sobrecarregado*.  Se você fizer isso, poderá controlar o comportamento de conversões de e para sua classe ou estrutura, incluindo as exceções que podem ser lançadas.  
  
## Sobrecarga  
 O operador `CType` também pode ser sobrecarregado em uma classe ou estrutura definida fora do seu código.  Se o seu código converte para ou a partir de tal classe ou estrutura, esteja certo de que entende o comportamento do seu operador `CType`.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Convertendo objetos dinâmicos  
 Conversões de tipos de objetos dinâmicos são executadas pela conversões dinâmicas definidas pelo usuário que usam os métodos de <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou de <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>.  Se você estiver trabalhando com objetos dinâmicos, use o método <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> para converter o objeto dinâmico.  
  
## Exemplo  
 O exemplo a seguir usa a função `CType` para converter uma expressão para o tipo de dados `Single`.  
  
 [!CODE [VbVbalrFunctions#24](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#24)]  
  
 Para exemplos adicionais, consulte [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## Consulte também  
 <xref:System.OverflowException>   
 <xref:System.InvalidCastException>   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Conversão de tipos no .NET Framework](../Topic/Type%20Conversion%20in%20the%20.NET%20Framework.md)