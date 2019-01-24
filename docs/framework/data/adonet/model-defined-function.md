---
title: função definida por modelo
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 371af3ae090e37cfd425a9e9d5946bb0751dc527
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538876"
---
# <a name="model-defined-function"></a>função definida por modelo
Um *função definida pelo modelo* é uma função que é definida em um modelo conceitual. O corpo de uma função definida pelo modelo é expresso em [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), que permite que a função ser expressa independentemente das regras ou idiomas com suporte na fonte de dados.  
  
 Uma definição de uma função definida modelo contém as informações a seguir:  
  
-   Um nome de função. (Necessário)  
  
-   O tipo do valor de retorno. (Opcional)  
  
    > [!NOTE]
    >  Se nenhum tipo de retorno for especificado, o valor de retorno é vago.  
  
-   Informações de parâmetro. (Opcional)  
  
-   Uma [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expressão que define o corpo da função.  
  
 Observe que as funções definidas modelo não suportam parâmetros de saída. Essa limitação é no lugar de modo que as funções definidas modelo podem ser compostos.  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.  
  
 ![Modelo com data publicada](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define uma função no modelo conceitual que retorna os números de anos como uma instância de `Book` (no diagrama anterior) foi publicado.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Consulte também
- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Modelo de dados de entidade: Tipos de dados primitivos](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
