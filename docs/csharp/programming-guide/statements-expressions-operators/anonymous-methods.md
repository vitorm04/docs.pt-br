---
title: Métodos anônimos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: d7823611df5e02040fd8735e1fa6ea7841298836
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595050"
---
# <a name="anonymous-methods-c-programming-guide"></a>Métodos anônimos (Guia de Programação em C#)
Nas versões anteriores ao C# 2.0, a única maneira de declarar um [delegado](../../../csharp/language-reference/keywords/delegate.md) era usar [métodos nomeados](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). O C# 2.0 apresentou os métodos anônimos e no C# 3.0 e versões posteriores, as expressões lambda substituem os métodos anônimos como a melhor maneira de gravar código embutido. No entanto, as informações sobre os métodos anônimos apresentadas neste tópico também se aplicam às expressões lambda. Há um caso em que um método anônimo fornece uma funcionalidade não encontrada em expressões lambda. Métodos anônimos habilitam a omissão da lista de parâmetros. Isso significa que um método anônimo pode ser convertido em delegados com uma variedade de assinaturas. Isso não é possível com expressões lambda. Para obter mais informações específicas sobre as expressões lambda, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Essencialmente, criar métodos anônimos é uma forma de passar um bloco de código como um parâmetro delegado. Veja dois exemplos:  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 Ao usar métodos anônimos, a sobrecarga de codificação será reduzida nos delegados instanciados, pois não é necessário criar um método separado.  
  
 Por exemplo, especificar um bloco de código em vez de um delegado pode ser útil em uma situação em que a criação de um método parece ser uma sobrecarga desnecessária. Um bom exemplo é quando um novo thread é iniciado. Essa classe cria um thread e também contém o código executado pelo thread sem criar um método adicional para o delegado.  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a>Comentários  
 O escopo dos parâmetros de um método anônimo é o *bloco de método anônimo*.  
  
 É um erro ter uma instrução de hiperlink, como [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), dentro do bloco de método anônimo se o destino estiver fora do bloco. Também é um erro ter uma instrução de hiperlink, como `goto`, `break` ou `continue`, fora do bloco de método anônimo se o destino estiver dentro do bloco.  
  
 As variáveis locais e parâmetros cujo escopo contém uma declaração de método anônimo são chamados variáveis *externas* do método anônimo. Por exemplo, no segmento de código a seguir, `n` é uma variável externa:  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 Uma referência à variável externa `n` é considerada *capturada* quando o delegado é criado. Ao contrário de variáveis locais, o tempo de vida de uma variável capturada se estende até os delegados que referenciam os métodos anônimos se tornarem elegíveis para a coleta de lixo.  
  
 Um método anônimo não pode acessar os parâmetros [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) e [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) de um escopo externo.  
  
 Nenhum código não seguro pode ser acessado dentro do *bloco de método anônimo*.  
  
 Os métodos anônimos não são permitidos no lado esquerdo do operador [is](../../../csharp/language-reference/keywords/is.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra duas maneiras de criar uma instância para um delegado:  
  
- Associando o delegado a um método anônimo.  
  
- Associando o delegado a um método nomeado (`DoWork`).  
  
 Em cada caso, uma mensagem será exibida quando o delegado for invocado.  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
- [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Delegados com métodos nomeados vs. métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
