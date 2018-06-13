---
title: Chamando funções em consultas no LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 690f1a2cdcd8726d40a6627c1ceb05c9ae7e7fdd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760135"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Chamando funções em consultas no LINQ to Entities
Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.  
  
 As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework. Para obter mais informações, consulte [como: chamar funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) e [como: chamar funções de banco de dados](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 O processo para chamar uma função personalizada exige três etapas básicas:  
  
1.  Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.  
  
2.  Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Chame a função em uma consulta LINQ to Entities.  
  
 Para obter mais informações, consulte os tópicos nesta seção.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como chamar funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Como chamar funções de banco de dados](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Como chamar funções de banco de dados personalizado](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Como chamar funções definidas em consultas](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Como chamar funções definidas por modelo como métodos de objeto](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Consulte também  
 [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)  
 [Visão geral do arquivo. edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Como: definir funções personalizadas no modelo conceitual](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
