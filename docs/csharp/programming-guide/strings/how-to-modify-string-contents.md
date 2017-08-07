---
title: "Como modificar o conteúdo de uma cadeia de caracteres (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 114b6fdabd235d7e57947e77b672352e28aff11e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>Como modificar o conteúdo de uma cadeia de caracteres (Guia de Programação em C#)
Como as cadeias de caracteres são *imutáveis*, não é possível (sem usar código não seguro) modificar o valor de um objeto de cadeia de caracteres depois que ele foi criado. No entanto, há várias maneiras de modificar o valor de uma cadeia de caracteres e armazenar o resultado em um novo objeto de cadeia de caracteres. A classe <xref:System.String?displayProperty=fullName> fornece métodos que operam em uma cadeia de caracteres de entrada e retornam um novo objeto de cadeia de caracteres. Em muitos casos, você pode atribuir o novo objeto à variável que mantinha a cadeia de caracteres original. A classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> fornece métodos adicionais que funcionam de maneira semelhante. A classe <xref:System.Text.StringBuilder?displayProperty=fullName> fornece um buffer de caracteres que você pode modificar "no local." Você chama o método <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> para criar um novo objeto de cadeia de caracteres que contém o conteúdo atual do buffer.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra várias maneiras para substituir ou remover subcadeias de caracteres em uma cadeia de caracteres especificada.  
  
 [!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Para acessar os caracteres individuais em uma cadeia de caracteres usando a notação de matriz, você pode usar o objeto <xref:System.Text.StringBuilder>, que sobrecarrega o operador `[]` para fornecer acesso ao seu buffer de caracteres interno. Você também pode converter a cadeia de caracteres em uma matriz de caracteres usando o método <xref:System.String.ToCharArray%2A>. O exemplo a seguir usa o método `ToCharArray` para criar a matriz. Alguns elementos dessa matriz são modificados. Um construtor de cadeia de caracteres que recebe uma matriz de char como um parâmetro de entrada é chamado para criar uma nova cadeia de caracteres.  
  
 [!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é fornecido para aquelas situações raras em que você talvez queira modificar uma cadeia de caracteres in-loco, usando código não seguro, de maneira semelhante a matrizes de caracteres de estilo C. O exemplo mostra como acessar os caracteres individuais "in-loco", usando a palavra-chave fixed. Ele também demonstra um possível efeito colateral das operações não seguras em cadeias de caracteres, que resultam da forma com que o compilador C# armazena (interna) as cadeias de caracteres internamente. Em geral, você não deve usar essa técnica, a menos que seja absolutamente necessário.  
  
 [!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)

