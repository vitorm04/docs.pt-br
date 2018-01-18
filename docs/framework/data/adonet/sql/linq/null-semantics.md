---
title: "Semântica nula"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="null-semantics"></a>Semântica nula
A tabela a seguir fornece links para diversas partes do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` (`Nothing` em [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) problemas são discutidos.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Tipos incompatíveis CLR do SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|“A seção de semântica nula” neste tópico inclui o exame de três estado SQL booleano dois estados contra o Common Language Runtime (CLR) <xref:System.Boolean>, `Nothing` literal ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) e `null` (C#), e outros problemas semelhantes.|  
|[Conversão de operador de consulta padrão](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[Métodos de System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.|  
|[Calcular a soma dos valores em uma sequência numérica](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliada como `null` (`Nothing` em [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) em vez de 0 para uma sequência que contém apenas valores nulos ou para uma sequência vazia.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
