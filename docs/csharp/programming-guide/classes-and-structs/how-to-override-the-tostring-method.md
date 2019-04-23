---
title: 'Como: substituir o método ToString – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 18734627e299c696e23bb0ec9bc63ed37fe3e601
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294971"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Como: substituir o método ToString (Guia de Programação em C#)
Cada classe ou struct no C# herda implicitamente a classe <xref:System.Object>. Portanto, cada objeto no C# obtém o método <xref:System.Object.ToString%2A>, que retorna uma representação de cadeia de caracteres desse objeto. Por exemplo, todas as variáveis do tipo `int` tem um método `ToString`, que permite retornar seus conteúdos como uma cadeia de caracteres:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Ao criar uma classe ou struct personalizada, é necessário substituir o método <xref:System.Object.ToString%2A> a fim de fornecer informações sobre o tipo ao código cliente.  
  
 Para obter informações sobre como usar cadeias de caracteres de formato e outros tipos de formatação personalizada com o método `ToString`, consulte [Tipos de Formatação](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Ao decidir quais informações devem ser fornecidas por meio desse método, considere se a classe ou struct será utilizado por código não confiável. Assegure-se de que nenhuma informação que possa ser explorada por código mal-intencionado seja fornecida.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Substituir o método ToString na classe ou struct  
  
1. Declare um método `ToString` com os seguintes modificadores e tipo retornado:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Implemente o método para que ele retorne uma cadeia de caracteres.  
  
     O exemplo a seguir retorna o nome da classe, além dos dados específicos de uma instância particular da classe.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     É possível testar o método `ToString`, conforme mostrado no exemplo de código a seguir:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IFormattable>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)
- [string](../../../csharp/language-reference/keywords/string.md)
- [new](../../../csharp/language-reference/keywords/new.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [Formatando Tipos](../../../standard/base-types/formatting-types.md)
