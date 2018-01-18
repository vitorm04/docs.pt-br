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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b0aa7f6f155de2c55f88b4c796ecc482d1cb84
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
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
