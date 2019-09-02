---
title: Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b0082b534b8df10ac5277cf2f5aa5b2d2e40c11b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204627"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="76c82-102">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="76c82-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="76c82-103">A linguagem de definição de esquema XML (XSD) permite que as restrições sejam especificadas nos elementos e atributos que ele define.</span><span class="sxs-lookup"><span data-stu-id="76c82-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="76c82-104">Ao mapear um esquema XML para o esquema relacional <xref:System.Data.DataSet>em um, as restrições de esquema XML são mapeadas para as restrições relacionais apropriadas nas tabelas e colunas dentro do **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="76c82-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="76c82-105">Esta seção discute o mapeamento das seguintes restrições de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="76c82-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="76c82-106">A restrição de exclusividade especificada usando o elemento **exclusivo** .</span><span class="sxs-lookup"><span data-stu-id="76c82-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="76c82-107">A restrição de chave especificada usando o elemento de **chave** .</span><span class="sxs-lookup"><span data-stu-id="76c82-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="76c82-108">A restrição keyref especificada usando o elemento **keyref** .</span><span class="sxs-lookup"><span data-stu-id="76c82-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="76c82-109">Usando uma restrição em um elemento ou atributo, você especifica determinadas restrições nos valores do elemento em qualquer instância do documento.</span><span class="sxs-lookup"><span data-stu-id="76c82-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="76c82-110">Por exemplo, uma restrição de chave em um elemento filho **CustomerID** de um elemento **Customer** no esquema indica que os valores do elemento filho **CustomerID** devem ser exclusivos em qualquer instância de documento e que os valores nulos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="76c82-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="76c82-111">As restrições também podem ser especificadas entre elementos e atributos em um documento, a fim de estabelecer uma relação dentro do documento.</span><span class="sxs-lookup"><span data-stu-id="76c82-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="76c82-112">As restrições Key e keyref são usadas no esquema para especificar as restrições dentro do documento, resultando em uma relação entre elementos de documento e atributos.</span><span class="sxs-lookup"><span data-stu-id="76c82-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="76c82-113">O processo de mapeamento converte essas restrições de esquema em restrições apropriadas nas tabelas criadas no **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="76c82-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76c82-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="76c82-114">In This Section</span></span>  
 [<span data-ttu-id="76c82-115">Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="76c82-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="76c82-116">Descreve os elementos de esquema XML usados para criar restrições exclusivas em um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="76c82-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="76c82-117">Mapear restrições de esquema XML (XSD) para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="76c82-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="76c82-118">Descreve os elementos de esquema XML usados para criar restrições de chave (restrições exclusivas em que valores NULL não são permitidos) em um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="76c82-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="76c82-119">Mapear restrições de keyref do esquema XML (XSD) para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="76c82-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="76c82-120">Descreve os elementos de esquema XML usados para criar restrições keyref (Foreign Key) em um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="76c82-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76c82-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="76c82-121">Related Sections</span></span>  
 [<span data-ttu-id="76c82-122">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="76c82-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="76c82-123">Descreve a estrutura relacional, ou esquema, de um **conjunto** de dados que é criado a partir do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="76c82-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="76c82-124">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="76c82-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="76c82-125">Descreve os elementos de esquema XML usados para criar relações entre colunas de tabela em um **conjunto**de uma.</span><span class="sxs-lookup"><span data-stu-id="76c82-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c82-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76c82-126">See also</span></span>

- <span data-ttu-id="76c82-127">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="76c82-127">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
