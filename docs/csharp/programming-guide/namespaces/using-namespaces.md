---
title: "Usando namespaces (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.names
dev_langs:
- CSharp
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 61b5d78f1c4924e3858c14876d36e52d4ee46ceb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-namespaces-c-programming-guide"></a>Usando namespaces (Guia de Programação em C#)
Os namespaces são usados intensamente em programas em C# de duas maneiras. Em primeiro lugar, as classes do .NET Framework usam namespaces para organizar suas muitas classes. Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.  
  
## <a name="accessing-namespaces"></a>Acessando namespaces  
 A maioria dos aplicativos do C# começam com uma seção de diretivas `using`. Essa seção lista os namespaces que o aplicativo usará com frequência e evita que o programador tenha que especificar um nome totalmente qualificado sempre que um método que está contido é usado.  
  
 Por exemplo, ao incluir a linha:  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 No início de um programa, o programador pode usar o código:  
  
 [!code-cs[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 Em vez de:  
  
 [!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Aliases de Namespace  
 A [diretiva using](../../../csharp/language-reference/keywords/using-directive.md) também pode ser usada para criar um alias para um [namespace](../../../csharp/language-reference/keywords/namespace.md). Por exemplo, se você estiver usando um namespace gravado anteriormente que contém namespaces aninhados, convém declarar um alias para fornecer uma forma abreviada de fazer referênia a um namespace em particular, como no exemplo a seguir:  
  
 [!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Usando namespaces para controlar o escopo  
 A palavra-chave `namespace` é usada para declarar um escopo. A capacidade de criar escopos dentro de seu projeto ajuda a organizar o código e permite que você crie tipos globalmente exclusivos. No exemplo a seguir, uma classe denominada `SampleClass` é definida em dois namespaces, um aninhado no outro. O [. Operador](../../../csharp/language-reference/operators/member-access-operator.md) é usado para diferenciar qual método será chamado.  
  
 [!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>Nomes totalmente qualificados  
 Os namespaces e os tipos têm títulos exclusivos descritos por nomes totalmente qualificados que indicam uma hierarquia lógica. Por exemplo, a instrução `A.B` implica que `A` é o nome do namespace ou do tipo e `B` é aninhado dentro dele.  
  
 No exemplo a seguir, há namespaces e classes aninhadas. O nome totalmente qualificado é indicado como um comentário após cada entidade.  
  
 [!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 No segmento de código anterior:  
  
-   O namespace `N1` é um membro do namespace global. Seu nome totalmente qualificado é `N1`.  
  
-   O namespace `N2` é um membro de `N1`. Seu nome totalmente qualificado é `N1.N2`.  
  
-   A classe `C1` é um membro de `N1`. Seu nome totalmente qualificado é `N1.C1`.  
  
-   O nome de classe `C2` é usado duas vezes nesse código. No entanto, os nomes totalmente qualificados são exclusivos. A primeira instância da `C2` é declarada dentro de `C1`, portanto, seu nome totalmente qualificado é: `N1.C1.C2`. A segunda instância da `C2` é declarada dentro de um namespace `N2`, portanto, seu nome totalmente qualificado é: `N1.N2.C2`.  
  
 Usando o segmento de código anterior, você pode adicionar um novo membro de classe `C3` ao namespace `N1.N2`, da seguinte maneira:  
  
 [!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 Em geral, use `::` para fazer referência a um alias de namespace ou `global::` para referenciar o namespace global e `.` para qualificar os tipos ou membros.  
  
 É um erro usar `::` com um alias que faz referência a um tipo em vez de um namespace. Por exemplo:  
  
 [!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Lembre-se que a palavra `global` não é um alias predefinido, portanto, `global.X` não tem qualquer significado especial. Ela só adquire um significado especial quando é usada com `::`.  
  
 O aviso do compilador CS0440 será gerado se você definir um alias chamado global porque `global::` sempre faz referência ao namespace global e não a um alias. Por exemplo, a linha a seguir gera o aviso:  
  
 [!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Usar `::` com aliases é uma boa ideia e protege contra a introdução inesperada de tipos adicionais. Considere este exemplo:  
  
 [!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 Isso funciona, mas se um tipo nomeado `Alias` fosse subsequentemente introduzido, `Alias.` se associaria a esse tipo. Usar `Alias::Exception` assegura que `Alias` seja tratado como um alias de namespace e não seja confundido com um tipo.  
  
 Consulte o tópico [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) para obter mais informações sobre o alias `global`.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Namespaces](../../../csharp/programming-guide/namespaces/index.md)   
 [Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. Operador](../../../csharp/language-reference/operators/member-access-operator.md)   
 [Operador ::](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)

