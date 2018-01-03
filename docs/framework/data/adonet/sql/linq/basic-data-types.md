---
title: "Tipos de dados básicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ae0bb07688cf1e9573d02826f186811cd7340c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-data-types"></a>Tipos de dados básicos
Porque as consultas LINQ to SQL traduzem a Transact-SQL antes que elas sejam executadas no Microsoft SQL Server. LINQ to SQL suporta grande parte da mesma funcionalidade interna que o SQL Server faz para tipos de dados básicos.  
  
## <a name="casting"></a>Conversão  
 Conversões implícitas ou explícitas estão ativados de um tipo de CLR de origem para um tipo de CLR de destino se há uma conversão válido semelhante em SQL Server. Para obter mais informações sobre conversão de CLR, consulte [função CType](~/docs/visual-basic/language-reference/functions/ctype-function.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) e [como](~/docs/csharp/language-reference/keywords/as.md). Após a conversão, conversões de alterar o comportamento de operações executadas em uma expressão CLR para corresponder ao comportamento de outras expressões de CLR que naturalmente mapear para o tipo de destino. Conversões também são traduzíveis no contexto de mapeamento de herança. Objetos podem ser convertidos em um subtipos mais específicos entidade para que seus dados específicos subtipo- possam ser acessados.  
  
## <a name="equality-operators"></a>Operadores de igualdade  
 LINQ to SQL oferece suporte aos seguintes operadores de igualdade em tipos de dados básicos dentro das consultas LINQ to SQL:  
  
-   Iguais e operador de desigualdade: Operadores de igualdade e desigualdade de são suportados para <xref:System.Boolean>numérico, <xref:System.DateTime>, e tipos de <xref:System.TimeSpan> . Para obter mais informações sobre [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] operadores `=` e `<>`, consulte [operadores de comparação](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Para obter mais informações sobre operadores de comparação do c# `==` e `!=`, consulte [operador = =](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) e [! = operador](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectivamente  
  
-   O operador: O operador de `IS` tem uma translação suportado quando o mapeamento de herança está sendo usado. Pode ser usado em vez de diretamente testar a coluna de discriminador para determinar se um objeto é de um tipo específico de entidade, e é convertido para uma verificação na coluna de discriminador. Para obter mais informações sobre os operadores do Visual Basic e c# é, consulte [operador Is](~/docs/visual-basic/language-reference/operators/is-operator.md) e [é](~/docs/csharp/language-reference/keywords/is.md).  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamento de tipo CLR do SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
