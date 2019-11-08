---
title: função definida por modelo
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 973d7ff9f7b76650782d62dcdcab60c8cedde18f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735584"
---
# <a name="model-defined-function"></a>função definida por modelo
Uma *função definida pelo modelo* é uma função que é definida em um modelo conceitual. O corpo de uma função definida pelo modelo é expresso em [Entity SQL](./ef/language-reference/entity-sql-language.md), o que permite que a função seja expressa independentemente das regras ou idiomas com suporte na fonte de dados.  
  
 Uma definição de uma função definida modelo contém as informações a seguir:  
  
- Um nome de função. (Necessário)  
  
- O tipo do valor de retorno. (Opcional)  
  
    > [!NOTE]
    > Se nenhum tipo de retorno for especificado, o valor de retorno é vago.  
  
- Informações de parâmetro. (Opcional)  
  
- Uma [Entity SQL](./ef/language-reference/entity-sql-language.md) expressão que define o corpo da função.  
  
 Observe que as funções definidas modelo não suportam parâmetros de saída. Essa limitação é no lugar de modo que as funções definidas modelo podem ser compostos.  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.  
  
 ![Captura de tela que mostra um modelo com a data de publicação.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define uma função no modelo conceitual que retorna os números de anos como uma instância de `Book` (no diagrama anterior) foi publicado.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
- [Modelo de Dados de Entidade: tipos de dados primitivos](entity-data-model-primitive-data-types.md)
