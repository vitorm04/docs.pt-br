---
title: 'Como: usar o alias de namespace global – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796280"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Como: usar o alias de namespace global (Guia de Programação em C#)
A capacidade de acessar um membro no [namespace](../../../csharp/language-reference/keywords/namespace.md) global é útil quando o membro estiver oculto por outra entidade com o mesmo nome.  
  
 Por exemplo, no código a seguir, `Console` resolve para `TestApp.Console` em vez de para o tipo `Console` no namespace <xref:System>.  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 Usar `System.Console` ainda resulta em um erro, pois o namespace `System` está oculto pela classe `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 No entanto, é possível contornar esse erro usando `global::System.Console`, assim:  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 Quando o identificador à esquerda for `global`, a pesquisa do identificador à direita começa no namespace global. Por exemplo, a declaração a seguir faz referência a `TestApp` como um membro do espaço global.  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 Obviamente, criar seus próprios namespaces chamados `System` não é recomendado e é improvável que qualquer código em que isso ocorra seja encontrado. No entanto, em projetos grandes, há uma possibilidade bem real de que a duplicação do namespace ocorra, de uma forma ou de outra. Nessas situações, o qualificador de namespace global é a garantia de que é possível especificar o namespace raiz.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Namespaces](../../../csharp/programming-guide/namespaces/index.md)
- [:: ??](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
