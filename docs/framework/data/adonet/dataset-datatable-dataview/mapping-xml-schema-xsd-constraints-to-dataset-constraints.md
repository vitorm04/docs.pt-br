---
title: "Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ac8e64c02d96450d41233cfbe65e1db839df9e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="ea5da-102">Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="ea5da-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="ea5da-103">A linguagem de definição de esquema XML (XSD) permite que sejam especificadas em elementos e atributos que define as restrições.</span><span class="sxs-lookup"><span data-stu-id="ea5da-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="ea5da-104">Ao mapear um esquema XML para esquema relacional em um <xref:System.Data.DataSet>, restrições de esquema XML são mapeadas para restrições relacionais apropriadas em tabelas e colunas dentro de **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="ea5da-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="ea5da-105">Esta seção descreve o mapeamento das seguintes restrições de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="ea5da-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="ea5da-106">A restrição de exclusividade especificada usando o **exclusivo** elemento.</span><span class="sxs-lookup"><span data-stu-id="ea5da-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="ea5da-107">A restrição de chave especificada usando o **chave** elemento.</span><span class="sxs-lookup"><span data-stu-id="ea5da-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="ea5da-108">A restrição keyref especificada usando o **keyref** elemento.</span><span class="sxs-lookup"><span data-stu-id="ea5da-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="ea5da-109">Usando uma restrição em um elemento ou atributo, você pode especificar algumas restrições nos valores do elemento em qualquer instância do documento.</span><span class="sxs-lookup"><span data-stu-id="ea5da-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="ea5da-110">Por exemplo, uma restrição de chave em um **CustomerID** elemento filho de um **cliente** elemento no esquema indica que os valores da **CustomerID** elemento filho deve ser exclusivo em qualquer instância de documento, e que não são permitidos valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ea5da-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="ea5da-111">Restrições também podem ser especificadas entre elementos e atributos em um documento, para estabelecer uma relação de dentro do documento.</span><span class="sxs-lookup"><span data-stu-id="ea5da-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="ea5da-112">As restrições de chave e keyref são usadas no esquema para especificar as restrições de dentro do documento, resultando em uma relação entre atributos e elementos de documento.</span><span class="sxs-lookup"><span data-stu-id="ea5da-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="ea5da-113">O processo de mapeamento converte essas restrições de esquema em restrições apropriadas nas tabelas criadas dentro de **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="ea5da-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea5da-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ea5da-114">In This Section</span></span>  
 [<span data-ttu-id="ea5da-115">Restrições de esquema XML (XSD) exclusivas mapa às restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="ea5da-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ea5da-116">Descreve os elementos de esquema XML usados para criar restrições exclusivas em um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="ea5da-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="ea5da-117">Restrições de esquema XML (XSD) às restrições de conjunto de dados de chave de mapa</span><span class="sxs-lookup"><span data-stu-id="ea5da-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ea5da-118">Descreve os elementos de esquema XML usados para criar restrições de chave (onde os valores nulos não são permitidos restrições exclusivas) em um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="ea5da-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="ea5da-119">Mapear keyref restrições de esquema XML (XSD) para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="ea5da-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ea5da-120">Descreve os elementos de esquema XML usados para criar keyref restrições (chave estrangeira) em um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="ea5da-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea5da-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ea5da-121">Related Sections</span></span>  
 [<span data-ttu-id="ea5da-122">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ea5da-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="ea5da-123">Descreve a estrutura relacional, ou o esquema, de um **conjunto de dados** que é criado a partir do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="ea5da-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="ea5da-124">Gerar relações de conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ea5da-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="ea5da-125">Descreve os elementos de esquema XML usados para criar relações entre colunas da tabela em uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="ea5da-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5da-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea5da-126">See Also</span></span>  
 <span data-ttu-id="ea5da-127">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ea5da-127">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
