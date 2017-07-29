---
title: "Métodos anônimos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
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
ms.openlocfilehash: 92842becf26a15ab1a6f5e9621002abf71dc67bc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="anonymous-methods-c-programming-guide"></a>Métodos anônimos (Guia de Programação em C#)
Nas versões anteriores ao C# 2.0, a única maneira de declarar um [delegado](../../../csharp/language-reference/keywords/delegate.md) era usar [métodos nomeados](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). O C# 2.0 apresentou os métodos anônimos e no C# 3.0 e versões posteriores, as expressões lambda substituem os métodos anônimos como a melhor maneira de gravar código embutido. No entanto, as informações sobre os métodos anônimos apresentadas neste tópico também se aplicam às expressões lambda. Há um caso em que um método anônimo fornece uma funcionalidade não encontrada em expressões lambda. Métodos anônimos habilitam a omissão da lista de parâmetros. Isso significa que um método anônimo pode ser convertido em delegados com uma variedade de assinaturas. Isso não é possível com expressões lambda. Para obter mais informações específicas sobre as expressões lambda, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Essencialmente, criar métodos anônimos é uma forma de passar um bloco de código como um parâmetro delegado. Veja dois exemplos:  
  
 [!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 Ao usar métodos anônimos, a sobrecarga de codificação será reduzida nos delegados instanciados, pois não é necessário criar um método separado.  
  
 Por exemplo, especificar um bloco de código em vez de um delegado pode ser útil em uma situação em que a criação de um método parece ser uma sobrecarga desnecessária. Um bom exemplo é quando um novo thread é iniciado. Essa classe cria um thread e também contém o código executado pelo thread sem criar um método adicional para o delegado.  
  
 [!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>Comentários  
 O escopo dos parâmetros de um método anônimo é o *bloco de método anônimo*.  
  
 É um erro ter uma instrução de hiperlink, como [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), dentro do bloco de método anônimo se o destino estiver fora do bloco. Também é um erro ter uma instrução de hiperlink, como `goto`, `break` ou `continue`, fora do bloco de método anônimo se o destino estiver dentro do bloco.  
  
 As variáveis locais e parâmetros cujo escopo contém uma declaração de método anônimo são chamados variáveis *externas* do método anônimo. Por exemplo, no segmento de código a seguir, `n` é uma variável externa:  
  
 [!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Uma referência à variável externa `n` é considerada *capturada* quando o delegado é criado. Ao contrário de variáveis locais, o tempo de vida de uma variável capturada se estende até os delegados que referenciam os métodos anônimos se tornarem elegíveis para a coleta de lixo.  
  
 Um método anônimo não pode acessar os parâmetros [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md) de um escopo externo.  
  
 Nenhum código não seguro pode ser acessado dentro do *bloco de método anônimo*.  
  
 Os métodos anônimos não são permitidos no lado esquerdo do operador [is](../../../csharp/language-reference/keywords/is.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra duas maneiras de criar uma instância para um delegado:  
  
-   Associando o delegado a um método anônimo.  
  
-   Associando o delegado a um método nomeado (`DoWork`).  
  
 Em cada caso, uma mensagem será exibida quando o delegado for invocado.  
  
 [!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Delegados com métodos nomeados vs. métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)

