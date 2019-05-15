---
title: Funções definidas pelo usuário
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: fb55a8b248b085275f83d47b1f452cd07bd8dcb1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582647"
---
# <a name="user-defined-functions"></a>Funções definidas pelo usuário
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usa métodos no seu modelo de objeto para representar funções definidas pelo usuário. Você designa métodos como funções aplicando o atributo de <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo de <xref:System.Data.Linq.Mapping.ParameterAttribute> . Para obter mais informações, consulte [o LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Para evitar <xref:System.InvalidOperationException>, funções definidas pelo usuário em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] devem estar em um das seguintes formas:  
  
- Uma função empacotada como um chamada de método que tem os atributos corretos de mapeamento. Para obter mais informações, consulte [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Um específico do método SQL estático a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Uma função com suporte por um método do .NET Framework.  
  
 Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo. Os desenvolvedores que usam o Visual Studio normalmente usaria o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear funções definidas pelo usuário.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Use as funções definidas pelo usuário com valor escalar](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Descreve como implementar uma função que retorna valores escalares.  
  
 [Como: Use as funções definidas pelo usuário com valor de tabela](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Descreve como implementar uma função que retorna apresentam valores.  
  
 [Como: Chamar funções definidas pelo usuário embutidas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Descreve como fazer chamadas a funções embutidas e as diferenças em execução quando o chamada é feita embutido.
