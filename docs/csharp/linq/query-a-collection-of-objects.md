---
title: "Consultar uma coleção de objetos"
description: "Como consultar coleções."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="query-a-collection-of-objects"></a>Consultar uma coleção de objetos
Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`. Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.  
  
 Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 Essa consulta é intencionalmente simples para que você possa testar. Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.  
  

## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)  
 [Cadeias de caracteres interpoladas](../language-reference/keywords/interpolated-strings.md)
