---
title: "função declarada por modelo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 85fb07b3577e7e61536664a346154ba9602cd9f3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="model-declared-function"></a><span data-ttu-id="e0dba-102">função declarada por modelo</span><span class="sxs-lookup"><span data-stu-id="e0dba-102">model-declared function</span></span>
<span data-ttu-id="e0dba-103">Um *função declarada por modelo* é uma função que é declarada em um modelo conceitual, mas não está definida no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e0dba-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="e0dba-104">A função pode ser definida no ambiente de hospedagem ou de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e0dba-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="e0dba-105">Por exemplo, uma função o declarada pode ser mapeada para uma função que está definida em uma base de dados, bem expõe a funcionalidade do lado do modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e0dba-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="e0dba-106">A declaração de uma função declarada modelo contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="e0dba-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="e0dba-107">O nome da função.</span><span class="sxs-lookup"><span data-stu-id="e0dba-107">The name of the function.</span></span> <span data-ttu-id="e0dba-108">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="e0dba-108">(Required)</span></span>  
  
-   <span data-ttu-id="e0dba-109">O tipo do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="e0dba-109">The type of the return value.</span></span> <span data-ttu-id="e0dba-110">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="e0dba-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0dba-111">Se nenhum valor de retorno for especificado, o tipo de retorno é vago.</span><span class="sxs-lookup"><span data-stu-id="e0dba-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="e0dba-112">Informações de parâmetro, incluindo o nome do parâmetro e o tipo.</span><span class="sxs-lookup"><span data-stu-id="e0dba-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="e0dba-113">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="e0dba-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0dba-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0dba-114">Example</span></span>  
 <span data-ttu-id="e0dba-115">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="e0dba-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e0dba-116">No CSDL, uma implementação de uma função declarada por modelo é um [importação de função](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="e0dba-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="e0dba-117">CSDL seguir define um contêiner de entidade com uma definição de importação de função.</span><span class="sxs-lookup"><span data-stu-id="e0dba-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="e0dba-118">Observe que o tipo de retorno da função é vago desde que nenhum tipo de retorno é especificado.</span><span class="sxs-lookup"><span data-stu-id="e0dba-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="e0dba-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0dba-119">See Also</span></span>  
 [<span data-ttu-id="e0dba-120">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="e0dba-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="e0dba-121">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="e0dba-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
