---
title: "const (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords: const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f54b686b170622ca1ead736a9f614c9bbef52dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="const-c-reference"></a>const (Referência de C#)
Use a palavra-chave `const` para declarar um campo constante ou um local constante. Campos e locais constantes não são variáveis ​​e não podem ser modificados. As constantes podem ser números, valores boolianos, cadeias de caracteres ou uma referência nula. Não crie uma constante para representar informações que você espera mudar a qualquer momento. Por exemplo, não use um campo constante para armazenar o preço de um serviço, um número de versão de produto ou a marca de uma empresa. Esses valores podem mudar ao longo do tempo e como os compiladores propagam constantes, outro código compilado com as bibliotecas terá que ser recompilado para ver as alterações. Veja também a palavra-chave [readonly](../../../csharp/language-reference/keywords/readonly.md). Por exemplo:  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a>Comentários  
 O tipo de uma declaração constante especifica o tipo dos membros que a declaração apresenta. O inicializador de um local ou um campo constante deve ser uma expressão constante que pode ser implicitamente convertida para o tipo de destino.  
  
 Uma expressão constante é uma expressão que pode ser completamente avaliada em tempo de compilação. Portanto, os únicos valores possíveis para as constantes de tipos de referência são `string` e uma referência nula.  
  
 A declaração constante pode declarar constantes múltiplas como:  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 O modificador `static` não é permitido em uma declaração constante.  
  
 A constante pode fazer parte de uma expressão constante, como a seguir:  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  A palavra-chave [readonly](../../../csharp/language-reference/keywords/readonly.md) é diferente da palavra-chave `const`. O campo `const` pode ser inicializado apenas na declaração do campo. Um campo `readonly` pode ser inicializado na declaração ou em um construtor. Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado. Além disso, embora um campo `const` seja uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como nesta linha: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como usar constantes como variáveis ​​locais.  
  
 [!code-csharp[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)
