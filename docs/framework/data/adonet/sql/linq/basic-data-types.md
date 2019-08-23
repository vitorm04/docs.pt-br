---
title: Tipos de dados básicos
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: b01a49afa99fc7ecdb7a113a5056e37d901527a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964073"
---
# <a name="basic-data-types"></a>Tipos de dados básicos
Porque as consultas LINQ to SQL traduzem a Transact-SQL antes que elas sejam executadas no Microsoft SQL Server. LINQ to SQL suporta grande parte da mesma funcionalidade interna que o SQL Server faz para tipos de dados básicos.  
  
## <a name="casting"></a>Conversão  
 Conversões implícitas ou explícitas estão ativados de um tipo de CLR de origem para um tipo de CLR de destino se há uma conversão válido semelhante em SQL Server. Para obter mais informações sobre a conversão de CLR, consulte [função CType](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) e [operadores de conversão e teste de tipo](../../../../../csharp/language-reference/operators/type-testing-and-cast.md). Após a conversão, as conversões alteram o comportamento das operações executadas em uma expressão CLR para corresponder ao comportamento de outras expressões CLR que são mapeadas naturalmente para o tipo de destino. As conversões também são traduzível no contexto do mapeamento de herança. Objetos podem ser convertidos em um subtipos mais específicos entidade para que seus dados específicos subtipo- possam ser acessados.  
  
## <a name="equality-operators"></a>Operadores de igualdade  
 LINQ to SQL oferece suporte aos seguintes operadores de igualdade em tipos de dados básicos dentro das consultas LINQ to SQL:  
  
- Operador de igual e desigualdade: Há suporte para operadores de igualdade e desigualdade para tipos <xref:System.Boolean>numéricos, <xref:System.TimeSpan> <xref:System.DateTime>, e. Para obter mais informações sobre `=` operadores `<>`de Visual Basic e, consulte [operadores de comparação](../../../../../visual-basic/language-reference/operators/comparison-operators.md). Para obter mais informações C# sobre operadores `==` de `!=`comparação e, consulte [operadores de igualdade](../../../../../csharp/language-reference/operators/equality-operators.md).
  
- É operador: O `IS` operador tem uma tradução com suporte quando o mapeamento de herança está sendo usado. Pode ser usado em vez de diretamente testar a coluna de discriminador para determinar se um objeto é de um tipo específico de entidade, e é convertido para uma verificação na coluna de discriminador. Para obter mais informações sobre os operadores C# Visual Basic e is, consulte [is Operator](../../../../../visual-basic/language-reference/operators/is-operator.md) and [is](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator).  
  
## <a name="see-also"></a>Consulte também

- [Mapeamento de tipo CLR do SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
