---
title: Classe Exception e suas propriedades
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 283b3b1aa0d56b50b6f9e67b66de3e0b68ae2331
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44216536"
---
# <a name="exception-class-and-properties"></a>Classe e propriedades da exceção

A classe <xref:System.Exception> é a classe base da qual as exceções herdam. Por exemplo, a hierarquia de classe <xref:System.InvalidCastException> é como se segue:

```
Object
  Exception
    SystemException
       InvalidCastException
```

A classe <xref:System.Exception> tem as propriedades a seguir, que ajudam a facilitar o entendimento de uma exceção.

| Nome da Propriedade | Descrição |
| ------------- | ----------- |
| <xref:System.Exception.Data> | Um <xref:System.Collections.IDictionary> que contém dados arbitrários em pares chave-valor. |
| <xref:System.Exception.HelpLink> | Pode conter uma URL (ou URN) para um arquivo de ajuda que fornece informações abrangentes sobre a causa de uma exceção. |
| <xref:System.Exception.InnerException> | Essa propriedade pode ser usada para criar e manter uma série de exceções durante o tratamento de exceção. Você pode usá-lo para criar uma nova exceção contendo exceções previamente capturadas. A exceção original pode ser capturada pela segunda exceção na propriedade <xref:System.Exception.InnerException>, permitindo que o código que trata da segunda exceção examine as informações adicionais. Por exemplo, suponha que você tem um método que recebe um argumento que está formatado de modo inadequado.  O código tenta ler o argumento, mas uma exceção é gerada. O método captura a exceção e gera um <xref:System.FormatException>. Para melhorar a capacidade do chamador para determinar o motivo pelo qual que uma exceção é gerada, às vezes é desejável que um método capture uma exceção gerada por uma rotina auxiliar e, em seguida, gere uma exceção mais indicativa do erro que ocorreu. Uma exceção mais nova e mais significativa pode ser criada, na qual a referência à exceção interna pode ser definida para a exceção original. Essa exceção mais significativa pode, em seguida, ser gerada para o chamador. Observe que com essa funcionalidade você pode criar uma série de exceções vinculadas que termina com a primeira exceção gerada. |
| <xref:System.Exception.Message> | Fornece detalhes sobre a causa de uma exceção.
| <xref:System.Exception.Source> | Obtém ou define o nome do aplicativo ou objeto que causa o erro. |
| <xref:System.Exception.StackTrace>| Contém um rastreamento de pilha que pode ser usado para determinar onde um erro ocorreu. O rastreamento de pilha inclui o nome do arquivo de origem e o número de linha de programa se informações de depuração estiverem disponíveis. |

A maioria das classes que herdam de <xref:System.Exception> não implementa membros adicionais nem fornece funcionalidade adicional; apenas herdam de <xref:System.Exception>. Portanto, as informações mais importantes para uma exceção podem ser encontradas na hierarquia de classes de exceção, no nome da exceção e nas informações contidas na exceção.

É recomendável gerar e capturar apenas objetos que derivam de <xref:System.Exception>, mas é possível gerar como uma exceção qualquer objeto que derive da classe <xref:System.Object>. Observe que nem todas as linguagens dão suporte à geração e captura de objetos que não derivam de <xref:System.Exception>.
  
## <a name="see-also"></a>Consulte também

- [Exceções](index.md)
