---
title: "Tipos anuláveis estruturados (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3f294088e92951e964c3daa2a105b767bca1d288
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="nullable-structured-types-entity-sql"></a>Tipos anuláveis estruturados (Entity SQL)
Uma instância de `null` de um tipo estruturada é uma instância que não existe. Isso é diferente de uma instância existente em que todas as propriedades têm valores de `null` .  
  
 Este tópico descreve os tipos estruturados anulável, incluindo que os tipos são anulável e que os padrões de código gerenciar instâncias de `null` de tipos anuláveis estruturados.  
  
## <a name="kinds-of-nullable-structured-types"></a>Tipos de tipos estruturados anulável  
 Existem três tipos de tipos anuláveis de framework:  
  
-   Tipos de linha.  
  
-   Tipos complexos.  
  
-   Tipos de entidade.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Os padrões de código que gerenciar instâncias nulos Structured tipo  
 Os seguintes cenários gerenciar instâncias de `null` :  
  
-   Na forma `null` como um tipo estruturada:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Upcasting de um tipo base para um tipo derivado:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Externo join à condição falsa:  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --ou  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --ou  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   Desreferenciando uma referência de `null` :  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   Obtendo ANYELEMENT de uma coleção vazia:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Verificar instâncias de `null` de tipos estruturados:  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
