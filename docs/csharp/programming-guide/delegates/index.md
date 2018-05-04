---
title: Delegados (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 516f5193509d3c87cc8fb7a36e2d69e04a85a6b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="delegates-c-programming-guide"></a>Delegados (Guia de Programação em C#)
Um [delegado](../../../csharp/language-reference/keywords/delegate.md) é um tipo que representa referências aos métodos com lista de parâmetros e tipo de retorno específicos. Ao instanciar um delegado, você pode associar sua instância a qualquer método com assinatura e tipo de retorno compatíveis. Você pode invocar (ou chamar) o método através da instância de delegado.  
  
 Delegados são usados para passar métodos como argumentos a outros métodos. Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados. Ao criar um método personalizado, uma classe como um controle do Windows poderá chamá-lo quando um determinado evento ocorrer. O seguinte exemplo mostra uma declaração de delegado:  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 Qualquer método de qualquer classe ou struct acessível que corresponda ao tipo delegado pode ser atribuído ao delegado. O método pode ser estático ou de instância. Isso possibilita alterar via programação chamadas de método e também conectar novo código a classes existentes.  
  
> [!NOTE]
>  No contexto da sobrecarga de método, a assinatura de um método não inclui o valor de retorno. No entanto, no contexto de delegados, a assinatura inclui o valor de retorno. Em outras palavras, um método deve ter o mesmo tipo de retorno que o delegado.  
  
 Essa capacidade de se referir a um método como um parâmetro torna delegados ideais para definir métodos de retorno de chamada. Por exemplo, uma referência a um método que compara dois objetos poderia ser passada como um argumento para um algoritmo de classificação. Como o código de comparação está em um procedimento separado, o algoritmo de classificação pode ser escrito de forma mais geral.  
  
## <a name="delegates-overview"></a>Visão geral de delegados  
 Os delegados possuem as seguintes propriedades:  
  
-   Os delegados são como ponteiros de funções em C++, mas apresentam tipos seguros.  
  
-   Os delegados permitem que métodos sejam passados como parâmetros.  
  
-   Os delegados podem ser usados para definir métodos de retorno de chamada.  
  
-   Os delegados podem ser encadeados juntos; por exemplo, vários métodos podem ser chamados um único evento.  
  
-   Os métodos não precisam corresponder ao tipo delegado exatamente. Para obter mais informações, consulte [Usando a variação delegados](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
-   O C# versão 2.0 introduziu o conceito de [Métodos Anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que permitem que blocos de código sejam passados como parâmetros em vez de um método definido separadamente. O C# 3.0 introduziu expressões lambda como uma maneira mais concisa de escrever blocos de código embutidos. Os métodos anônimos e as expressões lambda (em determinados contextos) são compilados para tipos delegados. Juntos, esses recursos são agora conhecidos como funções anônimas. Para obter mais informações sobre expressões lambda, consulte [Funções Anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Usando delegados](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [Quando usar delegados em vez de interfaces (Guia de Programação em C#)](http://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [Delegados com métodos nomeados vs. métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Usando Variação em Delegações](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Como combinar delegados (delegados multicast)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Como declarar e usar um delegado e criar uma instância dele](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Capítulos do Livro em Destaque  
 [Expressões lambda, eventos e delegados](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegados e eventos](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) em [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Delegate>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Eventos](../../../csharp/programming-guide/events/index.md)
