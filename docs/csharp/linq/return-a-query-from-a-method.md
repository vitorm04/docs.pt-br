---
title: "Retornar uma consulta de um método"
description: Como retornar uma consulta.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Como retornar uma consulta de um método (Guia de Programação em C#)
Este exemplo mostra como retornar uma consulta de um método como o valor retornado e como um parâmetro `out`.  
  
 Os objetos de consulta são combináveis, o que significa que você pode retornar uma consulta de um método. Os objetos que representam consultas não armazenam a coleção resultante, mas as etapas para gerar os resultados quando necessário. A vantagem de retornar objetos de consulta de métodos é que eles podem ser ainda mais modificados e combinados. Portanto, qualquer valor retornado ou parâmetro `out` de um método que retorna uma consulta também deve ter o tipo. Se um método materializa uma consulta em um tipo <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concreto, considera-se que ele está retornando os resultados da consulta em vez da consulta em si. Uma variável de consulta retornada de um método ainda pode ser combinada ou modificada.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o primeiro método retorna uma consulta como um valor retornado e o segundo método retorna uma consulta como um parâmetro `out`. Observe que em ambos os casos é uma consulta que é retornada, não os resultados da consulta.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)
