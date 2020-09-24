---
title: função declarada por modelo
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: fb30dd86c29d6a7fff6f2c71d5fd892326e1fda4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147847"
---
# <a name="model-declared-function"></a><span data-ttu-id="e2e04-102">função declarada por modelo</span><span class="sxs-lookup"><span data-stu-id="e2e04-102">model-declared function</span></span>

<span data-ttu-id="e2e04-103">Uma *função declarada por modelo* é uma função que é declarada em um modelo conceitual, mas não é definida nesse modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e2e04-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="e2e04-104">A função pode ser definida no ambiente de hospedagem ou de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e2e04-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="e2e04-105">Por exemplo, uma função o declarada pode ser mapeada para uma função que está definida em uma base de dados, bem expõe a funcionalidade do lado do modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e2e04-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="e2e04-106">A declaração de uma função declarada modelo contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2e04-106">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="e2e04-107">O nome da função.</span><span class="sxs-lookup"><span data-stu-id="e2e04-107">The name of the function.</span></span> <span data-ttu-id="e2e04-108">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="e2e04-108">(Required)</span></span>  
  
- <span data-ttu-id="e2e04-109">O tipo do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="e2e04-109">The type of the return value.</span></span> <span data-ttu-id="e2e04-110">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="e2e04-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e2e04-111">Se nenhum valor de retorno for especificado, o tipo de retorno é vago.</span><span class="sxs-lookup"><span data-stu-id="e2e04-111">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="e2e04-112">Informações de parâmetro, incluindo o nome do parâmetro e o tipo.</span><span class="sxs-lookup"><span data-stu-id="e2e04-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="e2e04-113">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="e2e04-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e04-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2e04-114">Example</span></span>  

 <span data-ttu-id="e2e04-115">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="e2e04-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="e2e04-116">No CSDL, uma implementação de uma função declarada por modelo é uma importação de função (usando o [elemento FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="e2e04-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="e2e04-117">CSDL seguir define um contêiner de entidade com uma definição de importação de função.</span><span class="sxs-lookup"><span data-stu-id="e2e04-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="e2e04-118">Observe que o tipo de retorno da função é vago desde que nenhum tipo de retorno é especificado.</span><span class="sxs-lookup"><span data-stu-id="e2e04-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="e2e04-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2e04-119">See also</span></span>

- [<span data-ttu-id="e2e04-120">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="e2e04-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="e2e04-121">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="e2e04-121">Entity Data Model</span></span>](entity-data-model.md)
