---
title: static (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a>static (Referência de C#)
Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico. O modificador `static` pode ser usado com classes, campos, métodos, propriedades, operadores, eventos e construtores, mas não pode ser usado com indexadores, finalizadores ou tipos diferentes de classes. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte classe é declarada como `static` e contém apenas métodos `static`:  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Uma constante ou declaração de tipo é, implicitamente, um membro estático.  
  
 Um membro estático não pode ser referenciado por meio de uma instância. Em vez disso, ele é referenciado pelo nome do tipo. Por exemplo, considere a seguinte classe:  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 Para fazer referência ao membro estático `x`, use o nome totalmente qualificado `MyBaseC.MyStruct.x`, a menos que o membro esteja acessível no mesmo escopo:  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Embora uma instância de uma classe contenha uma cópia separada de todos os campos de instância da classe, há apenas uma cópia de cada campo estático.  
  
 Não é possível usar [this](../../../csharp/language-reference/keywords/this.md) para referenciar métodos estáticos ou acessadores de propriedade.  
  
 Se a palavra-chave `static` for aplicada a uma classe, todos os membros da classe deverão ser estáticos.  
  
 As classes e as classes estáticas podem ter construtores estáticos. Os construtores estáticos são chamados em algum ponto entre o momento em que o programa é iniciado e a classe é instanciada.  
  
> [!NOTE]
>  A palavra-chave `static` tem utilizações mais limitadas do que no C++. Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).
  
 Para demonstrar os membros estáticos, considere uma classe que representa um funcionário da empresa. Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários. O método e o campo não pertencem a qualquer instância funcionário. Em vez disso, eles pertencem à classe empresa. Portanto, eles devem ser declarados como membros estáticos da classe.  
  
## <a name="example"></a>Exemplo  
 Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários. Para simplificar, este programa lê, do teclado, o número atual de funcionários. Em um aplicativo real, essas informações devem ser lidas de um arquivo.  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra que, embora seja possível inicializar um campo estático usando outro campo estático que ainda não foi declarado, os resultados serão indefinidos até que você atribua explicitamente um valor ao campo estático.  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
 [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
