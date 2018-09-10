---
title: Como Declarar e Usar Propriedades de Leitura e Gravação (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 77db2841d6ef9af21d38736f39e6041699ca13d5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44180241"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Como Declarar e Usar Propriedades de Leitura e Gravação (Guia de Programação em C#)
As propriedades oferecem a conveniência de membros de dados públicos sem os riscos associados ao acesso sem proteção, sem controle e não verificado aos dados de um objeto. Isso é feito por meio de *acessadores*: métodos especiais que atribuem e recuperam valores do membro de dados subjacente. O acessador [set](../../../csharp/language-reference/keywords/set.md) habilita a atribuição de membros de dados e o acessador [get](../../../csharp/language-reference/keywords/get.md) recupera valores do membro de dados.  
  
 Este exemplo mostra uma classe `Person` que tem duas propriedades: `Name` (string) e `Age` (int). Ambas as propriedades fornecem acessadores `get` e `set`, portanto, são consideradas propriedades de leitura/gravação.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
 No exemplo anterior, as propriedades `Name` e `Age` são [públicas](../../../csharp/language-reference/keywords/public.md) e incluem os acessadores `get` e `set`. Isso permite que qualquer objeto leia e grave essas propriedades. No entanto, às vezes é desejável excluir um os acessadores. Omitir o acessador `set`, por exemplo, torna a propriedade somente leitura:  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Como alternativa, é possível expor um acessador publicamente, porém, tornando o outro privado ou protegido. Para obter mais informações, consulte [Acessibilidade do Acessador Assimétrico](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Depois de serem declaradas, as propriedades podem ser usadas como campos da classe. Isso permite uma sintaxe muito natural na obtenção e configuração do valor de uma propriedade, conforme as instruções a seguir:  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Observe que em um método de propriedade `set`, uma variável especial `value` está disponível. Essa variável contém o valor que o usuário especificou, por exemplo:  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Observe a sintaxe normal para incrementar a propriedade `Age` em um objeto `Person`:  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Se métodos `set` e `get` separados fossem usados para modelar propriedades, o código equivalente se pareceria com isto:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 O método `ToString` é substituído neste exemplo:  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Observe que `ToString` não é usado explicitamente no programa. Ele é invocado por padrão pelas chamadas `WriteLine`.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)
