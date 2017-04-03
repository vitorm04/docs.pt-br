---
title: "dynamic (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- dynamic_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1c1202c29d5286c56ddb28e7277a01051b153485
ms.lasthandoff: 03/13/2017

---
# <a name="dynamic-c-reference"></a>dynamic (Referência de C#)
O tipo `dynamic` habilita operações nas quais ele ocorre para ignorar a verificação de tipo em tempo de compilação. Em vez disso, essas operações são resolvidas em tempo de execução. O tipo `dynamic` simplifica o acesso a APIs COM, como as APIs de Automação do Office e também às APIs dinâmicas, como bibliotecas do IronPython e ao Modelo de Objeto do Documento (DOM) do HTML.  
  
 O tipo `dynamic` se comporta como o tipo `object` na maioria das circunstâncias. No entanto, as operações que contêm expressões do tipo `dynamic` não são resolvidas ou verificadas pelo compilador. O compilador junta as informações sobre a operação em pacotes e, posteriormente, essas informações são usadas para avaliar a operação em tempo de execução. Como parte do processo, as variáveis do tipo `dynamic` são compiladas em variáveis do tipo `object`. Portanto, o tipo `dynamic` existe somente em tempo de compilação e não em tempo de execução.  
  
 O exemplo a seguir compara uma variável do tipo `dynamic` a uma variável do tipo `object`. Para verificar o tipo de cada variável no tempo de compilação, coloque o ponteiro do mouse sobre `dyn` ou `obj` nas instruções `WriteLine`. O IntelliSense mostra **dinâmico** para `dyn` e **objeto** para `obj`.  
  
 [!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 As instruções `WriteLine` exibem os tipos de tempo de execução de `dyn` e `obj`. Nesse ponto, ambos têm o mesmo tipo, inteiro. A saída a seguir será produzida:  
  
 `System.Int32`  
  
 `System.Int32`  
  
 Para ver a diferença entre `dyn` e `obj` em tempo de compilação, adicione as duas linhas a seguir entre as declarações e as instruções `WriteLine` no exemplo anterior.  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 Um erro de compilador será relatado em virtude da tentativa de adição de um inteiro e um objeto à expressão `obj + 3`. No entanto, nenhum erro será relatado para `dyn + 3`. A expressão contém `dyn` não é verificada em tempo de compilação, pois o tipo de `dyn` é `dynamic`.  
  
## <a name="context"></a>Contexto  
 A palavra-chave `dynamic` pode aparecer diretamente ou como um componente de um tipo construído nas seguintes situações:  
  
-   Em declarações, como o tipo de uma propriedade, campo, indexador, parâmetro, valor retornado, variável local ou restrição de tipo. A definição de classe a seguir usa `dynamic` em várias declarações diferentes.  
  
     [!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   Em conversões explícitas de tipo, como o tipo de destino de uma conversão.  
  
     [!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   Em qualquer contexto em que tipos sirvam como valores, como no lado direito de um operador `is` ou um operador `as` ou como o argumento para `typeof` como parte de um tipo construído. Por exemplo, `dynamic` pode ser usado nas expressões a seguir.  
  
     [!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `dynamic` em várias declarações. O método `Main` também compara a verificação de tipo em tempo de compilação com a verificação de tipo em tempo de execução.  
  
 [!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 Para obter mais informações e exemplos, consulte [Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Dynamic.ExpandoObject?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Como Executar a Conversão com Segurança Usando Operadores as e is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)   
 [Passo a passo: Criando e usando objetos dinâmicos](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
