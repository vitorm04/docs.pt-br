---
title: 'Como: usar o alias de namespace global – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: e01f8d5e8868c11a88d99c42fba06d8fefa5dc92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491682"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Como: usar o alias de namespace global (Guia de Programação em C#)
A capacidade de acessar um membro no [namespace](../../../csharp/language-reference/keywords/namespace.md) global é útil quando o membro estiver oculto por outra entidade com o mesmo nome.  
  
 Por exemplo, no código a seguir, `Console` resolve para `TestApp.Console` em vez de para o tipo `Console` no namespace <xref:System>.  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 Usar `System.Console` ainda resulta em um erro, pois o namespace `System` está oculto pela classe `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 No entanto, é possível contornar esse erro usando `global::System.Console`, assim:  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Quando o identificador à esquerda for `global`, a pesquisa do identificador à direita começa no namespace global. Por exemplo, a declaração a seguir faz referência a `TestApp` como um membro do espaço global.  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Obviamente, criar seus próprios namespaces chamados `System` não é recomendado e é improvável que qualquer código em que isso ocorra seja encontrado. No entanto, em projetos grandes, há uma possibilidade bem real de que a duplicação do namespace ocorra, de uma forma ou de outra. Nessas situações, o qualificador de namespace global é a garantia de que é possível especificar o namespace raiz.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o namespace `System` é usado para incluir a classe `TestClass`, portanto, `global::System.Console` deve ser usado para referenciar a classe `System.Console`, que está oculta pelo namespace `System`. Além disso, o alias `colAlias` é usado para fazer referência ao namespace `System.Collections`; portanto, a instância de um <xref:System.Collections.Hashtable?displayProperty=nameWithType> foi criada usando este alias em vez do namespace.  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
**A 1**
**B 2**
**C 3**

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Namespaces](../../../csharp/programming-guide/namespaces/index.md)
- [. ??](../../../csharp/language-reference/operators/member-access-operator.md)
- [:: ??](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
