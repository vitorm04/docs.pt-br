---
title: Usar namespaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 32e36a3ebc0de3e5f4a850e0af0261c1e7fd5a07
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039465"
---
# <a name="using-namespaces-c-programming-guide"></a>Usar namespaces (Guia de Programação em C#)

Os namespaces são usados intensamente em programas em C# de duas maneiras. Em primeiro lugar, as classes do .NET Framework usam namespaces para organizar suas muitas classes. Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.  
  
## <a name="accessing-namespaces"></a>Acessar namespaces

 A maioria dos aplicativos do C# começam com uma seção de diretivas `using`. Essa seção lista os namespaces que o aplicativo usará com frequência e evita que o programador tenha que especificar um nome totalmente qualificado sempre que um método que está contido é usado.  
  
 Por exemplo, ao incluir a linha:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 No início de um programa, o programador pode usar o código:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Em vez de:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>aliases de namespace

 Você também pode usar a [diretiva `using`](../../language-reference/keywords/using-directive.md) para criar um alias para um namespace. Use o [qualificador de alias de namespace `::`](../../language-reference/operators/namespace-alias-qualifier.md) para acessar os membros do namespace com alias. O exemplo a seguir mostra como criar e usar um alias de namespace:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Usar namespaces para controlar o escopo

 A palavra-chave `namespace` é usada para declarar um escopo. A capacidade de criar escopos dentro de seu projeto ajuda a organizar o código e permite que você crie tipos globalmente exclusivos. No exemplo a seguir, uma classe denominada `SampleClass` é definida em dois namespaces, um aninhado no outro. O [operador `.` de acesso de membro](../../language-reference/operators/member-access-operators.md#member-access-operator-) é usado para diferenciar qual método é chamado.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Nomes totalmente qualificados

 Os namespaces e os tipos têm títulos exclusivos descritos por nomes totalmente qualificados que indicam uma hierarquia lógica. Por exemplo, a instrução `A.B` implica que `A` é o nome do namespace ou do tipo e `B` é aninhado dentro dele.  
  
 No exemplo a seguir, há namespaces e classes aninhadas. O nome totalmente qualificado é indicado como um comentário após cada entidade.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 No segmento de código anterior:  
  
- O namespace `N1` é um membro do namespace global. Seu nome totalmente qualificado é `N1`.  
  
- O namespace `N2` é um membro de `N1`. Seu nome totalmente qualificado é `N1.N2`.  
  
- A classe `C1` é um membro de `N1`. Seu nome totalmente qualificado é `N1.C1`.  
  
- O nome de classe `C2` é usado duas vezes nesse código. No entanto, os nomes totalmente qualificados são exclusivos. A primeira instância da `C2` é declarada dentro de `C1`, portanto, seu nome totalmente qualificado é: `N1.C1.C2`. A segunda instância da `C2` é declarada dentro de um namespace `N2`, portanto, seu nome totalmente qualificado é: `N1.N2.C2`.  
  
 Usando o segmento de código anterior, você pode adicionar um novo membro de classe `C3` ao namespace `N1.N2`, da seguinte maneira:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Em geral, use o [qualificador de alias de namespace `::`](../../language-reference/operators/namespace-alias-qualifier.md) para fazer referência a um alias de namespace ou `global::` para fazer referência ao namespace global e `.` para qualificar tipos ou membros.  
  
 É um erro usar `::` com um alias que faz referência a um tipo em vez de um namespace. Por exemplo:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Lembre-se que a palavra `global` não é um alias predefinido, portanto, `global.X` não tem qualquer significado especial. Ela só adquire um significado especial quando é usada com `::`.  
  
 O aviso do compilador CS0440 será gerado se você definir um alias chamado global porque `global::` sempre faz referência ao namespace global e não a um alias. Por exemplo, a linha a seguir gera o aviso:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Usar `::` com aliases é uma boa ideia e protege contra a introdução inesperada de tipos adicionais. Considere este exemplo:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 Isso funciona, mas se um tipo nomeado `Alias` fosse subsequentemente introduzido, `Alias.` se associaria a esse tipo. O uso de `Alias::Exception` garante que `Alias` seja tratado como um alias de namespace e não seja confundido com um tipo.  

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Namespaces](../../../csharp/programming-guide/namespaces/index.md)
- [Operador .](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [Operador ::](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [Alias extern](../../../csharp/language-reference/keywords/extern-alias.md)
