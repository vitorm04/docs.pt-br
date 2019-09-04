---
title: Chamando funções em consultas no LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251258"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Chamando funções em consultas no LINQ to Entities
Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.  
  
 As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework. Para obter mais informações, confira [Como: Chame funções](how-to-call-canonical-functions.md) canônicas [e como: Chamar funções](how-to-call-database-functions.md)de banco de dados.  
  
 O processo para chamar uma função personalizada exige três etapas básicas:  
  
1. Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.  
  
2. Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Chame a função em uma consulta LINQ to Entities.  
  
 Para obter mais informações, consulte os tópicos nesta seção.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Chamar funções canônicas](how-to-call-canonical-functions.md)  
  
 [Como: Chamar funções de banco de dados](how-to-call-database-functions.md)  
  
 [Como: Chamar funções de banco de dados personalizadas](how-to-call-custom-database-functions.md)  
  
 [Como: Chamar funções definidas pelo modelo em consultas](how-to-call-model-defined-functions-in-queries.md)  
  
 [Como: Chamar funções definidas pelo modelo como métodos de objeto](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Consulte também

- [Consultas no LINQ to Entities](queries-in-linq-to-entities.md)
- [Canonical Functions](canonical-functions.md) (Funções canônicas)
- [Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Como: Definir funções personalizadas no modelo conceitual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
