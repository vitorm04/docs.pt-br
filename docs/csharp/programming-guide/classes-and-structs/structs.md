---
title: Structs – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 3f19d0485939e1923c479c1c9fdeb06572a11e14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240379"
---
# <a name="structs-c-programming-guide"></a>Structs (Guia de Programação em C#)

Structs são definidos usando a palavra-chave [struct](../../language-reference/keywords/struct.md), por exemplo:  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
Os structs compartilham a maioria da mesma sintaxe que as classes. O nome da struct deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#. Os structs são mais limitados do que as classes das seguintes maneiras:  
  
- Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como const ou estáticos.  
- Um struct não pode declarar um construtor padrão (um construtor sem parâmetros) ou um finalizador.  
- Os structs são copiados na atribuição. Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original. É importante se lembrar disso ao trabalhar com coleções de tipos de valor como `Dictionary<string, myStruct>`.  
- Os structs são tipos de valor, diferentemente das classes, que são tipos de referência.  
- Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.  
- Os structs podem declarar construtores que têm parâmetros. 
- Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe. Todos os structs herdam diretamente do <xref:System.ValueType>, que herda do <xref:System.Object>.  
- Um struct pode implementar interfaces.  
- Um struct pode ser usado como um tipo que permite valor nulo e pode receber um valor nulo.  
  
## <a name="related-sections"></a>Seções relacionadas  

Para saber mais:  
  
- [Usando structs](using-structs.md)
- [Construtores](constructors.md)
- [Tipos que permitem valor nulo](../nullable-types/index.md)
- [Como: saber a diferença entre passar um struct e passar uma referência de classe para um método](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [Como: implementar conversões definidas pelo usuário entre structs](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](index.md)
- [Classes](classes.md)
- [Nomes de identificadores](../inside-a-program/identifier-names.md)
