---
title: função definida por modelo
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934515"
---
# <a name="model-defined-function"></a><span data-ttu-id="5038f-102">função definida por modelo</span><span class="sxs-lookup"><span data-stu-id="5038f-102">model-defined function</span></span>
<span data-ttu-id="5038f-103">Uma *função definida pelo modelo* é uma função que é definida em um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="5038f-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="5038f-104">O corpo de uma função definida pelo modelo é expresso em [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), o que permite que a função seja expressa independentemente das regras ou idiomas com suporte na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5038f-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="5038f-105">Uma definição de uma função definida modelo contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="5038f-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="5038f-106">Um nome de função.</span><span class="sxs-lookup"><span data-stu-id="5038f-106">A function name.</span></span> <span data-ttu-id="5038f-107">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="5038f-107">(Required)</span></span>  
  
- <span data-ttu-id="5038f-108">O tipo do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="5038f-108">The type of the return value.</span></span> <span data-ttu-id="5038f-109">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="5038f-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5038f-110">Se nenhum tipo de retorno for especificado, o valor de retorno é vago.</span><span class="sxs-lookup"><span data-stu-id="5038f-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="5038f-111">Informações de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5038f-111">Parameter information.</span></span> <span data-ttu-id="5038f-112">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="5038f-112">(Optional)</span></span>  
  
- <span data-ttu-id="5038f-113">Uma [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expressão que define o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="5038f-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="5038f-114">Observe que as funções definidas modelo não suportam parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="5038f-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="5038f-115">Essa limitação é no lugar de modo que as funções definidas modelo podem ser compostos.</span><span class="sxs-lookup"><span data-stu-id="5038f-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5038f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5038f-116">Example</span></span>  
 <span data-ttu-id="5038f-117">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="5038f-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Captura de tela que mostra um modelo com a data de publicação.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="5038f-119">O [Entity Framework ADO.net](../../../../docs/framework/data/adonet/ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="5038f-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5038f-120">CSDL seguir define uma função no modelo conceitual que retorna os números de anos como uma instância de `Book` (no diagrama anterior) foi publicado.</span><span class="sxs-lookup"><span data-stu-id="5038f-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="5038f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5038f-121">See also</span></span>

- [<span data-ttu-id="5038f-122">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="5038f-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="5038f-123">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="5038f-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="5038f-124">Modelo de Dados de Entidade: Tipos de dados primitivos</span><span class="sxs-lookup"><span data-stu-id="5038f-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
