---
title: Como usar indexadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 4411fe0ffe7dc136b4e74adeba3e5596af3aa1db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589433"
---
# <a name="using-indexers-c-programming-guide"></a>Usando indexadores (Guia de Programação em C#)

Os indexadores são uma conveniência sintática que permitem criar uma [classe](../../language-reference/keywords/class.md), [struct](../../language-reference/keywords/struct.md) ou [interface](../../language-reference/keywords/interface.md) que os aplicativos clientes podem acessar como uma matriz. Os indexadores são implementados em tipos cuja principal finalidade é encapsular uma coleção ou matriz interna. Por exemplo, suponha que você tenha uma classe `TempRecord` que representa a temperatura em Fahrenheit, conforme registrada em 10 momentos diferentes durante um período de 24 horas. A classe contém uma matriz `temps` do tipo `float[]` para armazenar os valores de temperatura. Ao implementar um indexador nessa classe, os clientes podem acessar as temperaturas em uma instância `TempRecord` como `float temp = tr[4]`, e não como `float temp = tr.temps[4]`. A notação do indexador não simplifica somente a sintaxe para aplicativos clientes; ela também torna a classe e sua finalidade mais intuitivas para que os outros desenvolvedores entendam.  
  
Para declarar um indexador em uma classe ou struct, use a palavra-chave [this](../../language-reference/keywords/this.md), como mostra o seguinte exemplo:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Comentários

O tipo de um indexador e o tipo dos seus parâmetros devem ser pelo menos tão acessíveis quanto o próprio indexador. Para obter mais informações sobre níveis de acessibilidade, consulte [Modificadores de acesso](../../language-reference/keywords/access-modifiers.md).  
  
 Para obter mais informações sobre como usar indexadores com uma interface, consulte [Indexadores de Interface](./indexers-in-interfaces.md).  
  
 A assinatura de um indexador consiste do número e dos tipos de seus parâmetros formais. Ela não inclui o tipo de indexador nem os nomes dos parâmetros formais. Se você declarar mais de um indexador na mesma classe, eles terão diferentes assinaturas.  
  
 Um valor de indexador não é classificado como uma variável; portanto, não é possível passar um valor de indexador como um parâmetro [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Para fornecer o indexador com um nome que outras linguagens possam usar, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, como mostra o seguinte exemplo:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Este indexador terá o nome `TheItem`. Não fornecer o atributo de nome tornaria `Item` o nome padrão.  
  
## <a name="example-1"></a>Exemplo 1  
  
O exemplo a seguir mostra como declarar um campo de matriz privada, `temps` e um indexador. O indexador permite acesso direto à instância `tempRecord[i]`. A alternativa ao uso do indexador é declarar a matriz como um membro [público](../../language-reference/keywords/public.md) e acessar seus membros, `tempRecord.temps[i]`, diretamente.  
  
 Observe que, quando o acesso de um indexador é avaliado, por exemplo, em uma instrução `Console.Write`, o acessador [get](../../language-reference/keywords/get.md) é invocado. Portanto, se não existir nenhum acessador `get`, ocorrerá um erro em tempo de compilação.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Indexando usando outros valores

O C# não limita o tipo de parâmetro do indexador ao inteiro. Por exemplo, talvez seja útil usar uma cadeia de caracteres com um indexador. Esse indexador pode ser implementado pesquisando a cadeia de caracteres na coleção e retornando o valor adequado. Como os acessadores podem ser sobrecarregados, as versões do inteiro e da cadeia de caracteres podem coexistir.  
  
## <a name="example-2"></a>Exemplo 2  
  
O exemplo a seguir declara uma classe que armazena os dias da semana. Um acessador `get` aceita uma cadeia de caracteres, o nome de um dia e retorna o inteiro correspondente. Por exemplo, "Sunday" retorna 0, "Monday" retorna 1 e assim por diante.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Programação robusta

 Há duas maneiras principais nas quais a segurança e a confiabilidade de indexadores podem ser melhoradas:  
  
- Certifique-se de incorporar algum tipo de estratégia de tratamento de erros para manipular a chance de passagem de código cliente em um valor de índice inválido. Anteriormente, no primeiro exemplo neste tópico, a classe TempRecord oferece uma propriedade Length que permite que o código cliente verifique a saída antes de passá-la para o indexador. Também é possível colocador o código de tratamento de erro dentro do próprio indexador. Certifique-se documentar para os usuários as exceções que você gera dentro de um acessador do indexador.  
  
- Defina a acessibilidade dos acessadores [get](../../language-reference/keywords/get.md) e [set](../../language-reference/keywords/set.md) para que ela seja mais restritiva possível. Isso é importante para o acessador `set` em particular. Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Indexadores](./index.md)
- [Propriedades](../classes-and-structs/properties.md)
