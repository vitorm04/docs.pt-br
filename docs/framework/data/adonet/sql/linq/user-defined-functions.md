---
title: Funções definidas pelo usuário
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 061e07ba91a1742c90a594bf42f12e64172b2481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164110"
---
# <a name="user-defined-functions"></a>Funções definidas pelo usuário

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usa métodos no seu modelo de objeto para representar funções definidas pelo usuário. Você designa métodos como funções aplicando o atributo de <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo de <xref:System.Data.Linq.Mapping.ParameterAttribute> . Para obter mais informações, consulte [o modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md).  
  
 Para evitar <xref:System.InvalidOperationException>, funções definidas pelo usuário em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] devem estar em um das seguintes formas:  
  
- Uma função empacotada como um chamada de método que tem os atributos corretos de mapeamento. Para obter mais informações, consulte [mapeamento baseado em atributo](attribute-based-mapping.md).  
  
- Um específico do método SQL estático a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Uma função com suporte de um método .NET Framework.  
  
 Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo. Os desenvolvedores que usam o Visual Studio normalmente usariam o Object Relational Designer para mapear funções definidas pelo usuário.  
  
## <a name="in-this-section"></a>Nesta seção  

 [Como: usar funções definidas pelo usuário com valor escalar](how-to-use-scalar-valued-user-defined-functions.md)  
 Descreve como implementar uma função que retorna valores escalares.  
  
 [Como: usar funções definidas pelo usuário com valor de tabela](how-to-use-table-valued-user-defined-functions.md)  
 Descreve como implementar uma função que retorna apresentam valores.  
  
 [Como: chamar funções embutidas definidas pelo usuário](how-to-call-user-defined-functions-inline.md)  
 Descreve como fazer chamadas a funções embutidas e as diferenças em execução quando o chamada é feita embutido.
