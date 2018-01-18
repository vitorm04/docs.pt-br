---
title: tipo complexo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a7fbdace6403d2f1037beff8fe28d7c934d3174
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="complex-type"></a>tipo complexo
Um *tipo complexo* é um modelo para definir propriedades ricos, estruturadas em [tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md) ou em outros tipos complexos. Cada modelo contém o seguinte:  
  
-   Um nome exclusivo. (Necessário)  
  
    > [!NOTE]
    >  O nome de um tipo complexo não pode ser o mesmo que um nome de tipo de entidade dentro do mesmo namespace.  
  
-   Dados na forma de um ou mais [propriedades](../../../../docs/framework/data/adonet/property.md). (Opcional).  
  
    > [!NOTE]
    >  Uma propriedade de um tipo complexo pode ser outro tipo complexo.  
  
 Um tipo complexo é semelhante a um tipo de entidade que um tipo complexo pode levar uma carga útil de dados na forma das propriedades do tipo primitivo ou outros tipos complexos. No entanto, há algumas diferenças entre tipos complexos e tipos de entidade:  
  
-   Os tipos complexos não têm identidades e portanto não podem existir independente. Os tipos complexos podem existir somente como propriedades em tipos de entidade ou em outros tipos complexos.  
  
-   Tipos complexos não podem participar [associações](../../../../docs/framework/data/adonet/association-type.md). Nenhuma extremidade de uma associação pode ser um tipo complexo e, portanto, [propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) não podem ser definidos em tipos complexos.  
  
## <a name="example"></a>Exemplo  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um tipo complexo, endereço, com as propriedades `StreetAddress`, `City`, `StateOrProvince`, `Country`, e `PostalCode`de tipo primitivo.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Para definir o tipo complexo `Address` (acima) como uma propriedade em um tipo de entidade, você deve declarar a propriedade na definição de tipo de entidade. CSDL seguir declara a propriedade de `Address` como um tipo complexo em um tipo de entidade (Publisher):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
