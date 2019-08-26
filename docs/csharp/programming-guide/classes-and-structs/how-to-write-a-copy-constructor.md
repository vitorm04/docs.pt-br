---
title: 'Como: escrever um construtor de cópia – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596610"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Como: escrever um construtor de cópia (Guia de Programação em C#)
O C# não fornece um construtor de cópia para objetos, mas é possível escrever um por conta própria.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a `Person`[class](../../language-reference/keywords/class.md) define um construtor de cópia que usa, como seu argumento, uma instância de `Person`. Os valores das propriedades do argumento são atribuídos às propriedades da nova instância de `Person`. O código contém um construtor de cópia alternativa que envia as propriedades `Name` e `Age` da instância que você deseja copiar para o construtor de instância da classe.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ICloneable>
- [Guia de Programação em C#](../index.md)
- [Classes e Structs](./index.md)
- [Construtores](./constructors.md)
- [Finalizadores](./destructors.md)
