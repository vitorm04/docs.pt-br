---
title: Retornar uma consulta de um método
description: Como retornar uma consulta.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1c5fa534f3f39f8201d93b986e687d85bb303736
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473938"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Como retornar uma consulta de um método (Guia de Programação em C#)
Este exemplo mostra como retornar uma consulta de um método como o valor retornado e como um parâmetro `out`.  
  
 Os objetos de consulta são combináveis, o que significa que você pode retornar uma consulta de um método. Os objetos que representam consultas não armazenam a coleção resultante, mas as etapas para gerar os resultados quando necessário. A vantagem de retornar objetos de consulta de métodos é que eles podem ser ainda mais modificados e combinados. Portanto, qualquer valor retornado ou parâmetro `out` de um método que retorna uma consulta também deve ter o tipo. Se um método materializa uma consulta em um tipo <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concreto, considera-se que ele está retornando os resultados da consulta em vez da consulta em si. Uma variável de consulta retornada de um método ainda pode ser combinada ou modificada.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o primeiro método retorna uma consulta como um valor retornado e o segundo método retorna uma consulta como um parâmetro `out`. Observe que em ambos os casos é uma consulta que é retornada, não os resultados da consulta.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](index.md)
