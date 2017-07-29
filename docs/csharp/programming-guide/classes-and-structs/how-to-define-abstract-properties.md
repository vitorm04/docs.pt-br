---
title: "Como definir propriedades abstract (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: 13
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
ms.openlocfilehash: c6decaae138a21c24e94e2ed74111c860777f64b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Como definir propriedades abstract (Guia de Programação em C#)
O exemplo a seguir mostra como definir propriedades [abstract](../../../csharp/language-reference/keywords/abstract.md). Uma declaração de propriedade abstract não fornece uma implementação dos acessadores da propriedade – ela declara que a classe dá suporte às propriedades, mas deixa a implementação do acessador para classes derivadas. O exemplo a seguir demonstra como implementar as propriedades abstract herdadas de uma classe base.  
  
 Esse exemplo consiste em três arquivos, cada um deles é compilado individualmente e seu assembly resultante é referenciado pela próxima compilação:  
  
-   abstractshape.cs: a classe `Shape` que contém uma propriedade abstract `Area`.  
  
-   shapes.cs: as subclasses da classe `Shape`.  
  
-   shapetest.cs: um programa de teste para exibir as áreas de alguns objetos derivados de `Shape`.  
  
 Para compilar o exemplo, use o comando a seguir:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Isso criará o arquivo executável shapetest.exe.  
  
## <a name="example"></a>Exemplo  
 Esse arquivo declara a classe `Shape` que contém a propriedade `Area` do tipo `double`.  
  
 [!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Os modificadores da propriedade são colocados na própria declaração de propriedade. Por exemplo:  
  
    ```  
    public abstract double Area  
    ```  
  
-   Ao declarar uma propriedade abstract (como `Area` neste exemplo), você simplesmente indica quais acessadores de propriedade estão disponíveis, mas não os implementa. Neste exemplo, apenas um acessador [get](../../../csharp/language-reference/keywords/get.md) está disponível, assim, a propriedade é somente leitura.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra três subclasses de `Shape` e como elas substituem a propriedade `Area` para fornecer sua própria implementação.  
  
 [!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra um programa de teste que cria uma quantidade de objetos derivados de `Shape` e imprime suas áreas.  
  
 [!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Classes e membros de classes abstratas e lacradas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Como criar e usar assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)

