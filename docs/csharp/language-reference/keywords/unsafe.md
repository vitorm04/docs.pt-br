---
title: unsafe (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: f4fcff02166091ae5dbd83e7ddf7762373fd9836
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086447"
---
# <a name="unsafe-c-reference"></a>unsafe (Referência de C#)
A palavra-chave `unsafe` denota um contexto inseguro, que é necessário para qualquer operação que envolva ponteiros. Para obter mais informações, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 Você pode usar o modificador `unsafe` na declaração de um tipo ou membro. Toda a extensão textual do tipo ou membro é, portanto, considerada um contexto inseguro. Por exemplo, a seguir está um método declarado com o modificador `unsafe`:  
  
```csharp  
unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 O escopo do contexto inseguro se estende da lista de parâmetros até o final do método, portanto, os ponteiros também podem ser usados na lista de parâmetros:  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 Você também pode usar um bloco não seguro para habilitar o uso de um código não seguro dentro desse bloco. Por exemplo:  
  
```csharp  
unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Para compilar o código não seguro, você deve especificar a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md). O código não seguro não é verificável pelo Common Language Runtime.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [Buffers de tamanho fixo](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
