---
title: "Como usar ponteiros para copiar uma matriz de bytes (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Como usar ponteiros para copiar uma matriz de bytes (Guia de Programação em C#)
O exemplo a seguir usa ponteiros para copiar bytes de uma matriz para outra.  
  
 Este exemplo usa a palavra-chave [não seguro](../../../csharp/language-reference/keywords/unsafe.md), que permite que você use ponteiros no método `Copy`. A instrução [fixo](../../../csharp/language-reference/keywords/fixed-statement.md) é usada para declarar ponteiros para as matrizes de origem e de destino. Isso *fixa* o local das matrizes de origem e de destino na memória para que elas não sejam movidas pela coleta de lixo. Os blocos de memória para as matrizes não serão fixado quando o bloco `fixed` for concluído. Como o método `Copy` neste exemplo usa a palavra-chave `unsafe`, ele deve ser compilado com a opção do compilador **/unsafe**. Para definir a opção no Visual Studio, clique com botão direito do mouse no nome do projeto e, em seguida, clique em **Propriedades**. Na guia **Compilar**, selecione **Permitir código não seguro**.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [/unsafe (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [Coleta de lixo](../../../standard/garbage-collection/index.md)
