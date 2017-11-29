---
title: "Usando indexadores (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5c727edbbea116d858c6acf6b600f8fd9f43ee2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-indexers-c-programming-guide"></a>Usando indexadores (Guia de Programação em C#)
Os indexadores são uma conveniência sintática que permitem criar uma [classe](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md) ou [interface](../../../csharp/language-reference/keywords/interface.md) que os aplicativos clientes podem acessar como uma matriz. Os indexadores são implementados em tipos cuja principal finalidade é encapsular uma coleção ou matriz interna. Por exemplo, suponha que você tem uma classe nomeada TempRecord que representa a temperatura em Farenheit conforme registrada 10 vezes diferentes durante um período de 24 horas. A classe contém uma matriz nomeada “temps” de flutuação de tipo para representar as temperaturas e uma <xref:System.DateTime> que representa as datas em que as temperaturas foram registradas. Ao implementar um indexador nessa classe, os clientes podem acessar as temperaturas em uma instância TempRecord como `float temp = tr[4]` em vez de `float temp = tr.temps[4]`. A notação do indexador não simplifica somente a sintaxe para aplicativos clientes; ela também torna a classe e sua finalidade mais intuitivas para que os outros desenvolvedores entendam.  
  
 Para declarar um indexador em uma classe ou struct, use a palavra-chave [this](../../../csharp/language-reference/keywords/this.md), como neste exemplo:  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a>Comentários  
 O tipo de um indexador e o tipo dos seus parâmetros devem ser pelo menos tão acessíveis quanto o próprio indexador. Para obter mais informações sobre níveis de acessibilidade, consulte [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Para obter mais informações sobre como usar indexadores com uma interface, consulte [Indexadores de Interface](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 A assinatura de um indexador consiste do número e dos tipos de seus parâmetros formais. Ela não inclui o tipo de indexador nem os nomes dos parâmetros formais. Se você declarar mais de um indexador na mesma classe, eles terão diferentes assinaturas.  
  
 Um valor de indexador não é classificado como uma variável; portanto, não é possível passar um valor de indexador como um parâmetro [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  
  
 Para fornecer ao indexador um nome que outras linguagens possam usar, use um atributo `name` na declaração. Por exemplo:  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Este indexador terá o nome `TheItem`. Não fornecer o atributo de nome tornaria `Item` o nome padrão.  
  
## <a name="example-1"></a>Exemplo 1  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra como declarar um campo de matriz privada, `temps` e um indexador. O indexador permite acesso direto à instância `tempRecord[i]`. A alternativa ao uso do indexador é declarar a matriz como um membro [público](../../../csharp/language-reference/keywords/public.md) e acessar seus membros, `tempRecord.temps[i]`, diretamente.  
  
 Observe que, quando o acesso de um indexador é avaliado, por exemplo, em uma instrução `Console.Write`, o acessador [get](../../../csharp/language-reference/keywords/get.md) é invocado. Portanto, se não existir nenhum acessador `get`, ocorrerá um erro em tempo de compilação.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Indexando usando outros valores  
 O C# não limita o tipo de índice ao inteiro. Por exemplo, talvez seja útil usar uma cadeia de caracteres com um indexador. Esse indexador pode ser implementado pesquisando a cadeia de caracteres na coleção e retornando o valor adequado. Como os acessadores podem ser sobrecarregados, as versões do inteiro e da cadeia de caracteres podem coexistir.  
  
## <a name="example-2"></a>Exemplo 2  
  
### <a name="description"></a>Descrição  
 Neste exemplo, uma classe é declarada que armazena os dias da semana. Um acessador `get` é declarado que aceita uma cadeia de caracteres, o nome de um dia e retorna o inteiro correspondente. Por exemplo, domingo retornará 0, segunda-feira retornará 1 e assim por diante.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Há duas maneiras principais nas quais a segurança e a confiabilidade de indexadores podem ser melhoradas:  
  
-   Certifique-se de incorporar algum tipo de estratégia de tratamento de erros para manipular a chance de passagem de código cliente em um valor de índice inválido. Anteriormente, no primeiro exemplo neste tópico, a classe TempRecord oferece uma propriedade Length que permite que o código cliente verifique a saída antes de passá-la para o indexador. Também é possível colocador o código de tratamento de erro dentro do próprio indexador. Certifique-se documentar para os usuários as exceções que você gera dentro de um acessador do indexador.  
  
-   Defina a acessibilidade dos acessadores `get` e [set](../../../csharp/language-reference/keywords/set.md) para que ela seja o mais restritiva possível. Isso é importante para o acessador `set` em particular. Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)
