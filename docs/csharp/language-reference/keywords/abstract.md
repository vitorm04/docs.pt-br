---
title: abstract (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: d0a51afe61e75b750ed8bf336ca4636cb58dfbba
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43396893"
---
# <a name="abstract-c-reference"></a>abstract (Referência de C#)
O modificador `abstract` indica que o item que está sendo modificado tem uma implementação ausente ou incompleta. O modificador abstrato pode ser usado com classes, métodos, propriedades, indexadores e eventos. Use o modificador `abstract` em uma declaração de classe para indicar que uma classe destina-se apenas a ser uma classe base de outras classes. Membros marcados como abstratos ou incluídos em uma classe abstrata, devem ser implementados por classes que derivam da classe abstrata.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a classe `Square` deve fornecer uma implementação de `Area` porque deriva de `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 As classes abstratas têm os seguintes recursos:  
  
-   Uma classe abstrata não pode ser instanciada.  
  
-   Uma classe abstrata pode conter acessadores e métodos abstratos.  
  
-   Não é possível modificar uma classe abstrata com o modificador [sealed](../../../csharp/language-reference/keywords/sealed.md) porque os dois modificadores têm significados opostos. O modificador `sealed` impede que uma classe seja herdada e o modificador `abstract` requer uma classe a ser herdada.  
  
-   Uma classe não abstrata derivada de uma classe abstrata deve incluir implementações reais de todos os acessadores e métodos abstratos herdados.  
  
 Use o modificador `abstract` em uma declaração de método ou propriedade para indicar que o método ou propriedade não contem a implementação.  
  
 Os métodos abstratos têm os seguintes recursos:  
  
-   Um método abstrato é implicitamente um método virtual.  
  
-   Declarações de método abstrato são permitidas apenas em classes abstratas.  
  
-   Como uma declaração de método abstrato não fornece nenhuma implementação real, não há nenhum corpo de método, a declaração do método simplesmente termina com um ponto e vírgula e não há chaves ({ }) após a assinatura. Por exemplo:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     A implementação é fornecida por uma [substituição](../../../csharp/language-reference/keywords/override.md) de método, que é um membro de uma classe não abstrata.  
  
-   É um erro usar os modificadores [static](../../../csharp/language-reference/keywords/static.md) ou [virtual](../../../csharp/language-reference/keywords/virtual.md) em uma declaração de método abstrato.  
  
 Propriedades abstratas se comportam como métodos abstratos, exceto pelas diferenças na sintaxe de declaração e chamada.  
  
-   É um erro usar o modificador `abstract` em uma propriedade estática.  
  
-   Uma propriedade herdada abstrata pode ser substituída em uma classe derivada incluindo uma declaração de propriedade que usa o modificador [override](../../../csharp/language-reference/keywords/override.md).  
  
 Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Uma classe abstrata deve fornecer uma implementação para todos os membros de interface.  
  
 Uma classe abstrata que implementa uma interface pode mapear os métodos de interface em métodos abstratos. Por exemplo:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a classe `DerivedClass` é derivada de uma classe abstrata `BaseClass`. A classe abstrata contém um método abstrato, `AbstractMethod` e duas propriedades abstratas, `X` e `Y`.  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 No exemplo anterior, se você tentar instanciar a classe abstrata usando uma instrução como esta:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Você receberá uma mensagem de erro informando que o compilador não pode criar uma instância da classe abstrata "BaseClass".  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
- [virtual](../../../csharp/language-reference/keywords/virtual.md)  
- [override](../../../csharp/language-reference/keywords/override.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
