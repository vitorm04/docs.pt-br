---
title: Consultar uma coleção de objetos
description: Como consultar coleções.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: a62e5c6324d15376f1b42ad078eeb883b05ef14f
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
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
 [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md)
