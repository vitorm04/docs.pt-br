---
title: "dynamic (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "dynamic_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "dinâmica [C#]"
  - "palavra-chave dynamic [C#]"
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# dynamic (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `dynamic` tipo permite que as operações em que ele ocorre para ignorar a verificação de tipos em tempo de compilação.  Em vez disso, essas operações são resolvidas em tempo de execução.  O `dynamic` tipo simplifica o acesso às APIs COM, como as APIs de automação do Office e também para APIs dinâmicas, como bibliotecas de IronPython e para o HTML documento objeto DOM \(modelo\).  
  
 Tipo de `dynamic` se comporta como um tipo de `object` na maioria das circunstâncias.  No entanto, as operações que contenham expressões do tipo `dynamic` não foram resolvidos ou tipo marcado pelo compilador.  Os pacotes do compilador juntas informações sobre a operação e essas informações posteriormente é usada para avaliar a operação no tempo de execução.  Como parte do processo, variáveis do tipo `dynamic` são compilados em variáveis do tipo `object`.  Portanto, digite `dynamic` existe somente em tempo de compilação, não em tempo de execução.  
  
 O exemplo a seguir contrasta a uma variável do tipo `dynamic` a uma variável do tipo `object`.  Para verificar o tipo de cada variável em tempo de compilação, posicione o ponteiro do mouse sobre `dyn` ou `obj` na `WriteLine` instruções.  Apresentações de IntelliSense  **dinâmico** para `dyn` e  **objeto** para `obj`.  
  
 [!CODE [csrefKeywordsTypes#21](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#21)]  
  
 O `WriteLine` instruções exibem os tipos de tempo de execução de `dyn` e `obj`.  Nesse ponto, ambos têm o mesmo tipo, número inteiro.  A seguinte saída é produzida:  
  
 `System.Int32`  
  
 `System.Int32`  
  
 Para ver a diferença entre `dyn` e `obj` em tempo de compilação, adicione as duas linhas seguintes entre as declarações e o `WriteLine` instruções no exemplo anterior.  
  
```c#  
dyn = dyn + 3;  
obj = obj + 3;  
  
```  
  
 Um erro do compilador é relatado para a adição de tentativa de um número inteiro e um objeto na expressão `obj + 3`.  No entanto, nenhum erro é relatado para `dyn + 3`.  A expressão que contém `dyn` não é verificada quando da compilação porque o tipo de `dyn` é `dynamic`.  
  
## Contexto  
 O `dynamic` palavra\-chave pode ser exibidos diretamente ou como um componente de um tipo construído nas seguintes situações:  
  
-   Em declarações, como o tipo de uma propriedade, o campo, o indexador, o parâmetro, retornar o valor de variável local, ou digite a restrição.  Os seguintes usos de definição de classe `dynamic` em várias declarações diferentes.  
  
     [!CODE [csrefKeywordsTypes#22](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#22)]  
  
-   Em conversões de tipo explícito, como o tipo de destino de uma conversão.  
  
     [!CODE [csrefKeywordsTypes#23](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#23)]  
  
-   Em qualquer contexto em que tipos de servem como valores, como no lado direito de uma `is` operador ou uma `as` operador, ou como o argumento `typeof` como parte de um tipo construído.  Por exemplo, `dynamic` pode ser usado em expressões a seguir.  
  
     [!CODE [csrefKeywordsTypes#24](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#24)]  
  
## Exemplo  
 O exemplo a seguir usa `dynamic` em diversas declarações.  O `Main` método também contrasta a verificação com verificação de tipos em tempo de execução de tipos em tempo de compilação.  
  
 [!CODE [csrefKeywordsTypes#25](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#25)]  
  
 Para mais informações e exemplos, consulte [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
## Consulte também  
 <xref:System.Dynamic.ExpandoObject?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Como executar conversão cast com segurança usando operadores as e is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)   
 [Passo a passo: Criando e usando objetos dinâmicos](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)