---
title: Como escrever um construtor de cópia – guia de programação C#
description: Saiba como escrever um construtor de cópia em C# que usa uma instância da classe e retorna uma nova instância com os valores da entrada.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 52fd5aedea6a0e3b7c22e20db523329a00bba9ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204002"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Como escrever um construtor de cópia (guia de programação C#)

O C# não fornece um construtor de cópia para objetos, mas é possível escrever um por conta própria.  
  
## <a name="example"></a>Exemplo  

 No exemplo a seguir, a `Person`[class](../../language-reference/keywords/class.md) define um construtor de cópia que usa, como seu argumento, uma instância de `Person`. Os valores das propriedades do argumento são atribuídos às propriedades da nova instância de `Person`. O código contém um construtor de cópia alternativa que envia as propriedades `Name` e `Age` da instância que você deseja copiar para o construtor de instância da classe.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.ICloneable>
- [Guia de programação C#](../index.md)
- [Classes e structs](./index.md)
- [Construtores](./constructors.md)
- [Finalizadores](./destructors.md)
