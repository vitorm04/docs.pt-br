---
title: "Buffers de tamanho fixo (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Buffers de tamanho fixo (Guia de Programação em C#)
No C#, você pode usar a instrução [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados. Isso é útil quando você está trabalhando com o código existente, como código escrito em outras linguagens, DLLs preexistentes ou projetos COM. A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares. A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>Comentários  
 Em versões anteriores do C#, declarar uma estrutura de tamanho fixo no estilo do C++ era difícil porque um struct C# que contém uma matriz não contém os elementos da matriz. Em vez disso, o struct contém uma referência aos elementos.  
  
 O C# 2.0 adicionou a capacidade de inserir uma matriz de tamanho fixo em um [struct](../../../csharp/language-reference/keywords/struct.md) quando ele é usado em um bloco de código [não seguro](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Por exemplo, antes do C# 2.0, o seguinte `struct` teria um tamanho de 8 bytes. A matriz `pathName` é uma referência à matriz alocada em heap:  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 A partir do C# 2.0, um `struct` pode conter uma matriz inserida. No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo. Para acessar os elementos da matriz, você deve usar uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento. A instrução `fixed` fixa uma instância de `fixedBuffer` a um local específico na memória.  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 O tamanho da matriz `char` de 128 elementos é 256 bytes. Buffers de [char](../../../csharp/language-reference/keywords/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação. Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`. Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.  
  
 Outra matriz de tamanho fixo comum é a matriz [bool](../../../csharp/language-reference/keywords/bool.md). Os elementos em uma matriz `bool` sempre têm um byte de tamanho. Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.  
  
> [!NOTE]
>  Exceto pela memória criada usando [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), o compilador C# e o CLR (Common Language Runtime) não executam nenhuma verificação de estouro de buffer de segurança. Assim como acontece com qualquer código não seguro, tenha cuidado.  
  
 Buffers não seguros diferem de matrizes regulares das seguintes maneiras:  
  
-   Você só pode usar buffers não seguros em um contexto não seguro.  
  
-   Buffers não seguros sempre são vetores ou matrizes unidimensionais.  
  
-   A declaração de matriz deve incluir uma contagem, como `char id[8]`. Não é possível usar `char id[]`.  
  
-   Buffers não seguros só podem ser structs ou campos de instância em um contexto não seguro.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Interoperabilidade](../../../csharp/programming-guide/interop/index.md)
