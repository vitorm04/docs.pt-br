---
title: "Tratar exceções em expressões de consulta"
description: "Como tratar exceções em expressões de consulta."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a>Tratar exceções em expressões de consulta

É possível chamar qualquer método no contexto de uma expressão de consulta. No entanto, é recomendável que você evite chamar qualquer método em uma expressão de consulta que possa criar um efeito colateral, como modificar o conteúdo da fonte de dados ou gerar uma exceção. Este exemplo mostra como evitar gerar exceções ao chamar métodos em uma expressão de consulta, sem violar as diretrizes gerais sobre tratamento de exceção do .NET Framework. Essas diretrizes declaram que é aceitável capturar uma exceção específica quando você entende por que ela será lançada em um determinado contexto. Para obter mais informações, consulte [Melhores práticas para exceções](../../standard/exceptions/best-practices-for-exceptions.md).  
  
 O último exemplo mostra como tratar os casos em que é necessário lançar uma exceção durante a execução de uma consulta.  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir mostra como mover o código de tratamento de exceção para fora de uma expressão de consulta. Isso só é possível quando o método não depende de nenhuma variável que seja local para a consulta.  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a>Exemplo 

 Em alguns casos, a melhor resposta para uma exceção que é lançada de dentro de uma consulta poderá ser a interrupção imediata da execução da consulta. O exemplo a seguir mostra como tratar exceções que podem ser geradas de dentro de um corpo de consulta. Suponha que `SomeMethodThatMightThrow` possa causar uma exceção que exija que a execução da consulta seja interrompida.  
  
 Observe que o bloco `try` inclui o loop `foreach` e não a própria consulta. Isso ocorre porque o loop `foreach` é o ponto em que a consulta é realmente executada. Para obter mais informações, consulte [Introdução a consultas LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)
