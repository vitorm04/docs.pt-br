---
title: Delegados – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 80878ec1a592a368db246fc294ebc42556874832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921940"
---
# <a name="delegates-c-programming-guide"></a>Delegados (Guia de Programação em C#)
Um [delegado](../../language-reference/keywords/delegate.md) é um tipo que representa referências aos métodos com lista de parâmetros e tipo de retorno específicos. Ao instanciar um delegado, você pode associar sua instância a qualquer método com assinatura e tipo de retorno compatíveis. Você pode invocar (ou chamar) o método através da instância de delegado.  
  
 Delegados são usados para passar métodos como argumentos a outros métodos. Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados. Ao criar um método personalizado, uma classe como um controle do Windows poderá chamá-lo quando um determinado evento ocorrer. O seguinte exemplo mostra uma declaração de delegado:  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Qualquer método de qualquer classe ou struct acessível que corresponda ao tipo delegado pode ser atribuído ao delegado. O método pode ser estático ou de instância. Isso possibilita alterar via programação chamadas de método e também conectar novo código a classes existentes.  
  
> [!NOTE]
> No contexto da sobrecarga de método, a assinatura de um método não inclui o valor retornado. No entanto, no contexto de delegados, a assinatura inclui o valor retornado. Em outras palavras, um método deve ter o mesmo tipo de retorno que o delegado.  
  
 Essa capacidade de se referir a um método como um parâmetro torna delegados ideais para definir métodos de retorno de chamada. Por exemplo, uma referência a um método que compara dois objetos poderia ser passada como um argumento para um algoritmo de classificação. Como o código de comparação está em um procedimento separado, o algoritmo de classificação pode ser escrito de forma mais geral.  
  
## <a name="delegates-overview"></a>Visão geral de delegados  
 Os delegados têm as seguintes propriedades:  
  
- Representantes são semelhantes a ponteiros de função do C++, mas delegados são totalmente orientados a objeto e, ao contrário dos ponteiros de C++ para funções de membro, os delegados encapsulam uma instância do objeto e um método.
  
- Os delegados permitem que métodos sejam passados como parâmetros.  
  
- Os delegados podem ser usados para definir métodos de retorno de chamada.  
  
- Os delegados podem ser encadeados juntos; por exemplo, vários métodos podem ser chamados um único evento.  
  
- Os métodos não precisam corresponder ao tipo delegado exatamente. Para obter mais informações, confira [Usando a variação delegados](../concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- O C# versão 2.0 introduziu o conceito de [métodos anônimos](../../language-reference/operators/delegate-operator.md) que permitem que blocos de código sejam passados como parâmetros em vez de um método definido separadamente. O C# 3.0 introduziu expressões lambda como uma maneira mais concisa de escrever blocos de código embutidos. Os métodos anônimos e as expressões lambda (em determinados contextos) são compilados para tipos delegados. Juntos, esses recursos são agora conhecidos como funções anônimas. Para saber mais sobre expressões lambda, confira o artigo sobre [expressões lambda](../statements-expressions-operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>Nesta seção  
  
- [Usando delegados](./using-delegates.md)  
  
- [Quando usar delegados em vez de interfaces (Guia de Programação em C#)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Delegados com métodos nomeados vs. métodos anônimos](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Usando Variação em Delegações](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Como: combinar delegados (delegados multicast)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Como: declarar, instanciar e usar um delegado](./how-to-declare-instantiate-and-use-a-delegate.md)  

## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [Delegados](~/_csharplang/spec/delegates.md) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="featured-book-chapters"></a>Capítulos do Livro em Destaque  
 [Delegados, eventos e expressões lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) no [Manual de instruções C# 3.0, terceira edição: mais de 250 soluções para programadores do C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegados e eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) em [Aprendizado de C# 3.0: domine os princípios básicos de C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Delegate>
- [Guia de Programação em C#](../index.md)
- [Eventos](../events/index.md)
